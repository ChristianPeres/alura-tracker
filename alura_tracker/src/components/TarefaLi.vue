<template>
  <BoxCard>
    <div class="columns">
      <div class="column is-7">{{ tarefa.descricao ||'tarefa sem descricao'}}</div>
      <div class="column">
        <CronometroApp :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
        
      </div>
    </div>
  </BoxCard>
</template>
<script lang="ts">
import { defineComponent, PropType } from "vue";
import iTarefa from "../interfaces/iTarefa";
import CronometroApp from "./CronometroBar.vue";
import BoxCard from './BoxApp.vue'

export default defineComponent({
  name: "TarefaLista",
  components: {
    CronometroApp,
    BoxCard
  },
  props:{
    tarefa:{
      type: Object as PropType <iTarefa>,
        required: true
    }
  }
});
</script>
<style scoped>
.box{
  background: #5e5d5d;
}
</style>