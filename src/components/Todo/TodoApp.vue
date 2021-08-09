<template>
  <h1>{{ name }}</h1>

  <TodoForm />
  <TodoList />
</template>

<script>
import TodoForm from "./TodoForm.vue";
import TodoList from "./TodoList.vue";
import { provide, ref, watchEffect } from "vue";

export default {
  components: { TodoForm, TodoList },
  setup() {
    const name = "TODOS LIST";

    const todos = ref([]);
    provide("todos", todos);

    watchEffect(() => {
      console.log(todos.value.length);
      console.log(todos.value);
    });

    return {
      name,
    };
  },
};
</script>
