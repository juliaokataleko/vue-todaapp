<template>
    <div class="form-add">
        <form @submit="AddTodo">
            <input type="text" v-model="title" name="title" id=""
            placeholder="Adicionar tarefa"/>
            <input type="submit" class="btn"
            value="Guardar"/>
        </form>
    </div>
</template>



<script>

// import {v4 as uuidv4 } from 'uuid';

    export default {
        name: "AddTodo",
        data() {
            return {
                title: ''
            }
        },
        methods: {
            AddTodo(e) {
                e.preventDefault();
                const newTodo = {
                    title: this.title,
                    completed: false
                }

                // send up to parent
                this.$emit('add-todo', newTodo);
                this.title = '';
            }
        }
    }
</script>

<style scoped>

    form {
        display: flex;
    }

    .form-add {
        border-bottom: 0px solid #ddd;
    }

    input[type="text"] {
        flex: 10;
        padding: 0 10px;
        line-height: 2em;
        border: 0;
        background:#8bb1eb;
        color: #444;
    }

    input[type="submit"] {
        flex: 2;
        border: 0;
    }
    
</style>