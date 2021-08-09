<template>
  <div class="btn-group mt-2" role="group" aria-label="">
    <button type="button" @click="filtro('all')" class="btn btn-dark">
      All
    </button>
    <button type="button" @click="filtro('active')" class="btn btn-dark">
      Activos
    </button>
    <button type="button" @click="filtro('complete')" class="btn btn-dark">
      Terminado
    </button>
  </div>
</template>

<script>
import { inject } from "vue";
export default {
  setup() {
    const estado = inject("estado");
    console.log(estado.value);

    const filtro = (valor) => {
      estado.value = valor;
    };

    return { filtro };
  },
};
</script>

<style lang="scss" scoped>
</style>