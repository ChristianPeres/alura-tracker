<template>
  <section class="is-flex is-align-items-center is-justify-content-space-evenly">
    <CronometroApp :tempoEmSegundos="tempoEmSegundos"/>
    <ButtonComp @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
    <ButtonComp @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
  </section>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import CronometroApp from './CronometroBar.vue'
import ButtonComp from './Buttons.vue'

export default defineComponent({
  name: "TemporizadorApp",
  emits: ['aoTemporizadorFinalizado'],
  components: {
    CronometroApp,
    ButtonComp,
 
  },
  data() {
    return {
      tempoEmSegundos : 0,
      cronometro : 0,
      cronometroRodando: false
    }
  },

  methods: {
    iniciar() {
      this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 100);
    },
    finalizar() {
      this.cronometroRodando = false
      clearInterval(this.cronometro)
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
      this.tempoEmSegundos = 0
    }
  },
});
</script>
