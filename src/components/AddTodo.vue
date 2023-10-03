<template>
  <div>
    <input v-model="todoTitle" />
    <button @click="addNew">Add</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "AddTodo",
  setup(props, context) {
    const todoTitle = ref("");

    const addNew = () => {
      context.emit("item-add", todoTitle.value);
      todoTitle.value = "";
    };

    return {
      todoTitle,
      addNew,
    };
  },
};
</script>

<style>
</style>