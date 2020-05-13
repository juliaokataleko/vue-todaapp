<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p style="display: flex; flex-direction: row; 
        padding: 1em; align-items: center;
        justify-content: space-between;"> 
        
        <span>
            <label>
                <input type="checkbox" v-on:change="markComplete"/>
                {{ todo.title }}
            </label> </span>  
        <button @click="$emit('del-todo', todo.id)" class="del">X</button>
        </p>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props: ["todo"],
        methods: {
            markComplete() {
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>

    .todo-item {
        text-align: left;
        background: #f7f5f5;
        border-bottom: 1px #ccc solid;
    }

    .is-complete {
        background: #0ab875;
        color: #fff;
    }

    .del {
        background: #df3704;
        color: #fff;
        border: none;
        height: 35px;
        width: 35px;
        text-align: center;
        line-height: 35px;
        border-radius: 50%;
        cursor: pointer;
    }

    .del:hover {
        background: #aa634d;
    }

</style>