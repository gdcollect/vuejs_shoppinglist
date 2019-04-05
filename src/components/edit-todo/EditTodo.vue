<template>
  <div>
    <div class="card">
      <div class="card-body">
        <h3 class="text-center">Edit Todo</h3>
        <form @click="onUpdateTodo">
          <div class="form-group">
            <label for="name">Item</label>
            <input
              id="name"
              type="text"
              class="form-control"
              placeholder="Enter Item"
              v-model="todo.name"
            >
          </div>
          <div class="form-group">
            <label for="price">Price</label>
            <input
              id="price"
              type="text"
              class="form-control"
              placeholder="Enter Price"
              v-model="todo.price"
            >
          </div>
          <button type="submit" class="btn btn-block btn-success">UPDATE</button>
        </form>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "edit-todo",
  data() {
    return {};
  },
  props: {
    todo: Object
  },

  methods: {
    onUpdateTodo(e) {
      e.preventDefault();
      this.$emit("update-todo", this.$props.todo);
    }
  }
};
</script>



<style scoped>
</style>
