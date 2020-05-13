<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <div class="load" v-if="loading">Carregando...</div>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>

import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';

import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [],
      loading: false
    }
  },
  methods: {
    deleteTodo(id) {
      this.loading = true;
      axios.get('http://localhost:8000/todo/delete/'+id)
      .then(res => {
        this.todos = res.data.todos;
         console.log(res.data);
         this.loading = false;
      })
      .catch(err => console.log(err));

      // this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.loading = true;
      const { title, completed } = newTodo;
      axios.post('http://localhost:8000/todo/store', {
        title, completed
      })
      .then(res => {
        if(res.data.OK) {
          this.todos = res.data.todos;
        }
        console.log(res.data);
        this.loading = false;
      })
      .catch(err => console.log(err));

      // this.todos = [...this.todos, newTodo];
    }
  },
  created(){
    this.loading = true;
    axios.get('http://localhost:8000/todos')
      .then(res => {
        this.todos = res.data.todos;
         console.log(res.data);
         this.loading = false;
      })
      .catch(err => console.log(err));
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding:0;
}

body {
  font-family: arial;
  line-height: 1.4;
}

.load {
  background: green;
  text-align: center;
  color: #fff;
  line-height: 3em;
  bottom: 3px;
  right: 3px;
  left: 3px;
  margin: 0 auto;
  width: 180px;
  position: fixed;
  z-index: 222222;
}

.btn {
  display: inline-block;
  border: none;
  background:#194fc4;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #777;
}
</style>

