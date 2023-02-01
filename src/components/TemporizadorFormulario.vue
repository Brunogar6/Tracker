<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
      <Cronometro-Formulario :tempoEmSegundos="tempoEmSegundos"/>
      <BotaoFormulario @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando"/>
      <BotaoFormulario @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando"/>
    </div>
</template>

<script>
import CronometroFormulario from "@/components/CronometroFormulario.vue";
import BotaoFormulario from "@/components/BotaoFormulario.vue";

export default {
  name: "TemporizadorFormulario",
  emits: ['aoTemporizadorFinalizado'],
  components: {
    BotaoFormulario,
    CronometroFormulario
  },
  data() {
    return {
      tempoEmSegundos : 0,
      cronometro: 0,
      cronometroRodando: false
    }
  },
  methods: {
    iniciar() {
      this.cronometroRodando = true
      this.cronometro = setInterval(() =>   {
        this.tempoEmSegundos += 1

      }, 1000)
    },
    finalizar() {
      this.cronometroRodando = false
      clearInterval(this.cronometro)
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
      this.tempoEmSegundos = 0
    }
  }
}
</script>