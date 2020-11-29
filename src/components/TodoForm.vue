<template>
  <form @submit.prevent="formulario">
    <input
      class="form-control my-3"
      type="text"
      placeholder="Crea una nueva tarea"
      v-model.trim="texto"
    />
  </form>
</template>

<script>
import { inject, ref } from "vue";
export default {
  setup() {
    const todos = inject("todos");
    const texto = ref("");
    const formulario = () => {
      console.log(texto.value);

      if (texto.value === "") {
        console.log("esta vacío");
        return;
      }
      const todo = {
        texto: texto.value,
        estado: false,
        id: Date.now(),
      };
      todos.value.push(todo);
      console.log(todos.value);

      texto.value = "";
      console.log(todo.value);
    };
    return { formulario, texto };
  },
};
</script>

<style>
</style>