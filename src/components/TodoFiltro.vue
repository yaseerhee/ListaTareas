<template>
  <div class="card mt-3 d-flex justify-content-between">
    <div class="card-body d-flex justify-content-between">
      <span role="button" @click="filtrar('activos')">Por hacer</span>
      <span role="button" @click="filtrar('all')">Todas Las Tareas</span>
      <span role="button" @click="filtrar('completado')">Solo Completadas</span>
    </div>
  </div>
</template>

<script>
import { inject } from "vue";
export default {
  setup() {
    const estado = inject("estado");

    const filtrar = (valor) => {
      estado.value = valor;
    };

    return { filtrar };
  },
};
</script>

<style>
</style>