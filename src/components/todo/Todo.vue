<template>
  <div id="todo">
    <div v-for="todo in todos" v-bind:key="todo.id">
      <TodoItem
        v-on:get-todo="$emit('get-todo', todo)"
        v-on:toggle-edit="toggleEdit"
        v-on:delete-todo="$emit('delete-todo', todo.id)"
        v-bind:todo="todo"
      />
    </div>
  </div>
</template>


<script>
import TodoItem from "../todo-item/TodoItem";

export default {
  name: "todo",
  props: {
    todos: Array
  },
  components: {
    TodoItem
  },
  methods: {
    toggleEdit(isToggle) {
      this.$emit("toggle-edit", isToggle);
    }
  }
};
</script>


<style scoped>
</style>
