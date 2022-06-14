<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          aria-label="Nome da tarefa"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
      <TemporizadorForm @aoTemporizadorFinalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorForm from './TemporizadorForm.vue';

export default defineComponent({
  name: 'FormulárioPrincipal',
  components: {
    TemporizadorForm,
  },
  data() {
    return {
      descricao: '',
    };
  },
  methods: {
    finalizarTarefa(tempoDecorrido: number) : void {
      console.log(tempoDecorrido);
      console.log(this.descricao);
      this.descricao = '';
    },
  },
});
</script>

<style scope>
/* Style for the sidebar */
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
