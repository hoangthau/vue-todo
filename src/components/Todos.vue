<template>
  <div>
    <AddTodo v-on:item-add="handleAdd" />
    <TodoItem
      v-for="todo in todos"
      v-bind:key="todo.id"
      :todoProps="todo"
      v-on:item-changed="changeStatus"
      v-on:item-deleted="handleDelete"
    />
  </div>
</template>

<script>
import { ref } from "vue";

import TodoItem from "./TodoItem.vue";
import AddTodo from "./AddTodo.vue";

export default {
  name: "TodoList",
  components: {
    TodoItem,
    AddTodo,
  },
  setup() {
    const todos = ref([
      { id: 1, title: "Viec 1", completed: false },
      { id: 2, title: "Viec 2", completed: false },
      { id: 3, title: "Viec 3", completed: false },
    ]);

    const changeStatus = (id) => {
      todos.value = todos.value.map((todo) => {
        if (todo.id === id) {
          return {
            ...todo,
            completed: !todo.completed,
          };
        }
        return todo;
      });
    };

    const handleDelete = (id) => {
      todos.value = todos.value.filter((todo) => todo.id !== id);
    };

    const handleAdd = (title) => {
      const length = todos.value.length;
      todos.value.push({ id: length + 1, title, completed: false });
    };

    return {
      todos,
      changeStatus,
      handleDelete,
      handleAdd,
    };
  },
};
</script>

<style>
</style>