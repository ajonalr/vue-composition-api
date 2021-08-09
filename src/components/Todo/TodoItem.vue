<template>
  <li class="list-group-item d-flex justify-content-between">
    <span role="button" :class="{'tachado': todo.estado}" @click="completado(todo.id)"
      >{{ todo.texto }}
    </span>
    <i
      class="fa fa-trash"
      aria-hidden="true"
      style="color: red"
      role="button"
      @click="eliminar(todo.id)"
    ></i>
  </li>
</template>

<script>
import { inject } from "vue";
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },

  setup() {
    const todos = inject("todos");

    const eliminar = (id) => {
      todos.value = todos.value.filter((item) => item.id !== id);
    };

    const completado = (id) => {
      todos.value = todos.value.map((item) => {
        if (item.id === id) {
          item.estado = true;
        }
        return item;
      });
    };

    return {
      eliminar,
      completado,
    };
  },
};
</script>

<style scoped>
.tachado {
  text-decoration: line-through;
}
</style>
