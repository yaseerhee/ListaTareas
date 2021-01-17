<template>
  <div class="container">
    <h1 class="titulo-1">Lista de Tareas</h1>
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
@import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");

body{
  background-color: #2a9d8f;
}

.container {
  margin: 10%;
  font-family: "Roboto", sans-serif;
}

.titulo-1 {
  font-size: 56px;
  color: #264653;
  text-align: center;
}
</style>