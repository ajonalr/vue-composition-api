<template>
  <ul class="list-group">
    <todo-item v-for="todo in todos" :key="todo.id" :todo="todo" />
    <todo-footer v-if="todos.length > 0" />
    <li class="list-group-item d-flex justify-content-between active" v-else>
      No Hay Elementos
    </li>

    <todo-filtro />
  </ul>
</template>

<script>
import { inject, ref, computed, provide } from "vue";
import TodoFooter from "./TodoFooter.vue";
import TodoItem from "./TodoItem.vue";
import TodoFiltro from "./TodoFiltro.vue";
export default {
  components: {
    TodoFooter,
    TodoItem,
    TodoFiltro,
  },
  setup() {
    const todosTodos = inject("todos");
    const estado = ref('all');
    provide('estado', estado);

    const todos = computed(() => {
      if (estado.value === 'all') {
        return todosTodos.value
      }
      if (estado.value === 'active') {
        return todosTodos.value.filter(item => item.estado === false);
      }
      if (estado.value === 'complete') {
        return todosTodos.value.filter(item => item.estado === true);
      } 
    })
    return {
      todos,
    };
  },
};
</script>
