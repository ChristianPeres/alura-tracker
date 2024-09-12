<template>
  <main class="columns is-multiline" :class="{ 'modo-claro': modoClaroAtivo }">
    <div class="columns is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <formularioBar @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefaLista v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <BoxCard v-if="ListaEstaVazia">
          voce nao esta produtivo hj
        </BoxCard>
      </div>
    </div> 
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from './components/BarraLateral.vue' 
import formularioBar from './components/FormularioApp.vue';
import TarefaLista from './components/TarefaLi.vue';
import iTarefa from './interfaces/iTarefa'
import BoxCard from './components/BoxApp.vue'

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    formularioBar,
    TarefaLista,
    BoxCard
  },
  data (){
    return{
      tarefas: [] as iTarefa[],
      modoClaroAtivo: false
    }
  },
  computed: {
    ListaEstaVazia() : boolean{
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa (tarefa: iTarefa) {
      this.tarefas.push(tarefa)
    },
    trocarTema(modoClaroAtivo: boolean){
      this.modoClaroAtivo = modoClaroAtivo
    }
  }
}); 
</script>
<style>
.lista{
  padding: 1.25rem;
}
main.modo-claro{
--bg-primario: #fff;
--texto-primario: #000;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>


