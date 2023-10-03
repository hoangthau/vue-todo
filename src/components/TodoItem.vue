<template>
  <p :class="{ done: todoProps.completed }">
    <input type="checkbox" v-on:change="changeTodoItem" />
    {{ todoProps.title }}
    <button @click="deleteTodoItem">Delete</button>
  </p>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todoProps"],
  setup(props, context) {
    const changeTodoItem = () => {
      context.emit("item-changed", props.todoProps.id);
    };

    const deleteTodoItem = () => {
      context.emit("item-deleted", props.todoProps.id);
    };

    return {
      changeTodoItem,
      deleteTodoItem,
    };
  },
};
</script>

<style>
.done {
  color: green;
  text-decoration: line-through;
}
</style>