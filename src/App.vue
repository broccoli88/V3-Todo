<template>
    <h1>TODO List</h1>
    <Todo />
</template>

<script>
import Todo from "./components/Todo.vue";

export default {
    name: "App",
    components: { Todo },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: black;
    margin-top: 60px;
}
</style>


