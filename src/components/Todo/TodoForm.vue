<template>
  <form @submit.prevent="addTarea()">
    <div class="mb-3">
      <input
        v-model.trim="text"
        type="text"
        class="form-control"
        placeholder="INSERTE TODO"
      />
    </div>
  </form>
</template>

<script>
import { inject, ref } from "vue";
export default {
  setup() {
    const text = ref("");
    const todos = inject("todos");

    const addTarea = () => {
      if (text.value === "") {
        console.log("Esta Basio");
        return;
      }

      const todo = {
        texto: text.value,
        estado: false,
        id: Date.now(),
      };

      todos.value.push(todo);
      text.value = "";
      // console.log(todos.value);
    };

    return {
      addTarea,
      text,
    };
  },
};
</script>
