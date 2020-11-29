<template>
  <div class="container">
    <h1>ToDo List</h1>
    <todo-form />
    <todo-list />
  </div>
</template>

<script>
import { provide, ref, watchEffect } from "vue";
import TodoForm from "./TodoForm.vue";
import TodoList from "./TodoList.vue";
export default {
  components: { TodoForm, TodoList },
  setup() {
    //Esto nos ayuda a referenciar el todo para almacenar los valores del
    // formulario
    const todos = ref([]);
    provide("todos", todos);

    if (localStorage.getItem("todos")) {
      todos.value = JSON.parse(localStorage.getItem("todos"));
    }

    watchEffect(() => {
      console.log(todos.value.length);
      console.log(todos.value);
      localStorage.setItem("todos", JSON.stringify(todos.value));
    });
  },
};
</script>

<style>
</style>