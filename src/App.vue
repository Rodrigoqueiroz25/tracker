<template>
  <main class="columns is-gapeless is-multiline" :class="{'modo-escuro': modoEscuro}">
    <div class="column is-one-quarter without-padding">
      <BarraLateral @temaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioTarefas @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <Box v-if="listaVazia">
          Você não está muito produtivo hoje :(
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import BarraLateral from './components/BarraLateral.vue';
  import FormularioTarefas from './components/FormularioTarefas.vue';
  import Tarefa from './components/Tarefa.vue';
  import ITarefa from './interfaces/ITarefa';
  import Box from './components/Box.vue';

  export default defineComponent({
    name: "App",
    components: {
    BarraLateral,
    FormularioTarefas,
    Tarefa,
    Box
  },

  computed: {
    listaVazia() : boolean {
      return this.tarefas.length === 0
    }
  },

  data(){
    return {
      tarefas: [] as ITarefa[],
      modoEscuro: false
    }
  },

  methods: {
    salvarTarefa(tarefa: ITarefa){
      this.tarefas.push(tarefa);
    },
    trocarTema(modoEscuro: boolean){
      this.modoEscuro = modoEscuro;
    }
  }

  });
</script>

<style>

  .lista{
    padding: 1.25rem;
  }

  main{
    --bg-primario: #fff;
    --texto-primario: #000;
  }

  main.modo-escuro{
    --bg-primario: #2b2d42;
    --texto-primario: #ddd;
  }

  .conteudo{
    background-color: var(--bg-primario);
  }

  .without-padding{
    padding: 0rem;
  }

</style>
