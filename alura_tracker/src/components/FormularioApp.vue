<template>
  <div class="box formulario">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="formulario para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa voce deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <TemporizadorApp @aoTemporizadorFinalizado="finalizarTarefa"/>
    </div>
  </div>
  </div>
</template> 
<script lang="ts">
import { defineComponent } from "vue";
import TemporizadorApp from './Temporizador.vue'

export default defineComponent({
  name: "formularioBar",
  components: {
    TemporizadorApp
    
  },
  emits: ['aoSalvarTarefa'],

  methods: {
    finalizarTarefa(tempoDecorrido: number) :void {
      this.$emit('aoSalvarTarefa', {
        duracaoEmSegundos: tempoDecorrido,
        descricao: this.descricao
      })
      this.descricao = ''
      
      
    }
  },
  data (){
    return{
      descricao: ''
    }
  }
  
});
</script>
<style>
.formulario {
  color: var(--texto-primario);

}
.box{
  color: rgb(204, 204, 204);
}
</style>