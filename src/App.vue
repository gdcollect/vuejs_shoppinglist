<template>
  <div id="app">
    <Header class="header" v-bind:heading="heading"/>
    <br><br><br><br><br>
    <div class="container">
      <div class="app-content">
        <div v-show="!isToggle">
          <AddTodo v-on:add-todo="onAddTodo"/>
        </div>
        <div v-show="isToggle">
          <span @click="isToggle = !isToggle" class="close btn-close text-danger">&times;</span>
          <EditTodo v-bind:todo="todo" v-on:update-todo="onUpdateTodo"/>
        </div>
        <br>
        <Todo
          v-on:delete-todo="onDeleteTodo"
          v-on:get-todo="getTodo"
          v-on:toggle-edit="toggleEdit"
          v-bind:todos="todos"
        />
      </div>
    </div>
    <hr>
    <Footer/>
  </div>
</template>

<script>
import uuid from "uuid";

import Header from "./components/layouts/header/Header";
import Todo from "./components/todo/Todo";
import AddTodo from "./components/add-todo/AddTodo";
import EditTodo from "./components/edit-todo/EditTodo";
import Footer from "./components/layouts/footer/Footer";

export default {
  name: "app",
  data() {
    return {
      heading: "Shopping List",
      isToggle: null,
      todo: {},
      todos: [
        {
          id: uuid.v4(),
          name: "playing cart",
          price: 22.99
        },
        {
          id: uuid.v4(),
          name: "head watch",
          price: 25.99
        }
      ]
    };
  },
  components: {
    Header,
    Todo,
    AddTodo,
    EditTodo,
    Footer
  },
  methods: {
    onAddTodo(newTodo) {
      this.todos.push(newTodo);
    },

    toggleEdit(checkToggle) {
      this.isToggle = checkToggle;
    },

    getTodo(todo) {
      this.todo = todo;
    },

    onUpdateTodo(newTodo) {
      if (newTodo.name !== null || newTodo.price !== null) {
        let index = this.todos.indexOf(this.todo);
        if (index !== -1) {
          this.todos[index] = newTodo;
        }
      } else {
        alert(`Please fill out these fields...`);
      }
    },

    onDeleteTodo(id) {
      let isOk = confirm("Are you sure you want to remove it..??");
      if (isOk) {
        this.todos = this.todos.filter(todo => {
          return todo.id !== id;
        });
      }
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  line-height: 1.5;
  font-weight: 400;
  font-size: 1rem;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  overflow-x: hidden;
}

.app-content {
  width: 70%;
  margin: auto;
}

.btn-close {
  position: relative;
  top: -1rem;
  font-size: 2rem;
  cursor: pointer;
}

.header {
  position: fixed;
  width: 100%;
  z-index: 100;
}
</style>
