<template>
  <Header title="My Todo list" />
  <TodoList />
</template>

<script>
import Header from "./components/Header.vue";
import TodoList from "./components/Todos.vue";

export default {
  name: "App",
  components: {
    Header,
    TodoList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
