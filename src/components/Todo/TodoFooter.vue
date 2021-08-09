<template>
  <li class="list-group-item d-flex justify-content-between">
    <span role="button"> Todos Activos: <b>{{contarActivos}}</b>  </span>

    <span role="button" @click="deleteComplete()">Eliminar Completados</span>
  </li>
</template>

<script>
import { inject, computed } from "vue";
export default {
  setup() {
    const todos = inject("todos");
    const contarActivos = computed(() => {
       return todos.value.filter(item => item.estado === false).length
    });

    const deleteComplete = () => {
       todos.value = todos.value.filter(item => item.estado === false);
    }

    return {
       contarActivos,
       deleteComplete
    };
  },
};
</script>

<style lang="scss" scoped>
</style>