<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <FormularioPrincipal />
      <div class="lista">
        <TarefaFormulario />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import FormularioPrincipal from './components/FormularioPrincipal.vue';
import TarefaFormulario from './components/TarefaFormulario.vue';
import ITarefa from './interfaces/ITarefa';
export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioPrincipal,
    TarefaFormulario
  },
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  }
});

</script>

<style>

</style>
