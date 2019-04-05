<template>
  <div>
    <div class="card">
      <div class="card-body">
        <h3 class="text-center">Add Todo</h3>
        <form @submit="onAddTodo">
          <div class="form-group">
            <label for="name">Item</label>
            <input
              id="name"
              v-model="name"
              type="text"
              class="form-control"
              placeholder="Enter Item"
            >
          </div>
          <div class="form-group">
            <label for="price">Price</label>
            <input
              id="price"
              v-model="price"
              type="text"
              class="form-control"
              placeholder="Enter Price"
            >
          </div>
          <button type="submit" class="btn btn-block btn-success">ADD</button>
        </form>
      </div>
    </div>
  </div>
</template>


<script>
import uuid from "uuid";

export default {
  name: "add-todo",
  data() {
    return {
      name: "",
      price: ""
    };
  },
  methods: {
    onAddTodo(e) {
      e.preventDefault();
      let newTodo = {
        id: uuid.v4(),
        name: this.name,
        price: this.price
      };
      if (newTodo.name === "" || newTodo.price === "") {
        alert(`Please fill out all fields...`);
      } else {
        this.$emit("add-todo", newTodo);
        this.name = "";
        this.price = "";
      }
    }
  }
};
</script>



<style scoped>
</style>
