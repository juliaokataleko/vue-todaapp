<template>
    <header class="header">
        <h1>Lista de Tarefas</h1>
        <div>
            <router-link to="/">Inicio</router-link> |
            <router-link to="/about">Sobre</router-link>
        </div>
    </header>
</template>

<script>
    export default {
        name: "Header",
    }
</script>

<style scoped>

    .header {
        background:#468af0;
        color: #fff;
        text-align: center;
        line-height: 5em;
        padding: 0 2em;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        font-size: 12px;
        text-transform: uppercase;
    }

    .header a {
        color: #fff;
        padding-right: 5px;
        text-decoration: none;
    }
    
</style>