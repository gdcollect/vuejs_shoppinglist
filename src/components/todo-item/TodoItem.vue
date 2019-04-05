<template>
  <div id="todo-item">
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item">
            <strong>Name</strong>
            <span class="float-right">{{todo.name}}</span>
          </li>
          <li class="list-group-item">
            <strong>Price</strong>
            <span class="float-right">{{`$${todo.price}`}}</span>
          </li>
        </ul>
      </div>
      <div class="card-footer">
        <button @click="onHandleEdit" class="btn btn-dark mr-1">EDIT</button>
        <button @click="$emit('delete-todo', todo.id)" class="btn btn-danger">DELETE</button>
      </div>
    </div>
    <br>
  </div>
</template>


<script>
export default {
  name: "todo-item",
  data() {
    return {
      toggleEdit: false
    };
  },
  props: {
    todo: Object
  },
  methods: {
    onHandleEdit() {
      this.toggleEdit = !this.toggleEdit;
      this.$emit("toggle-edit", this.toggleEdit);
      this.$emit("get-todo", this.$props.todo);
    }
  }
};
</script>


<style scoped>
</style>
