<template>
  <li class="list-group-item d-flex justify-content-between">
    <span role="button"> {{ contarActivos }} Activos </span>
    <span role="button" @click="eliminarCompletados()">
      Eliminar Completados
    </span>
  </li>
</template>

<script>
import { computed, inject } from "vue";
export default {
  setup() {
    const todos = inject("todos");

    const contarActivos = computed(() => {
      return todos.value.filter((item) => item.estado === false).length;
    });

    const eliminarCompletados = () => {
      todos.value = todos.value.filter((item) => item.estado === false);
    };

    return { contarActivos, eliminarCompletados };
  },
};
</script>

<style>
</style>