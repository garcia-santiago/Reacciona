<template>
  <h1>Juego de Reacción</h1>
  
  <button @click="start" :disabled="this.playing">Jugar</button>

  <Block v-if="this.playing" :delay="this.delay" @end="endGame"/>

  <Mensaje v-show="mostrarMensaje" :score="score"/>

  <Top v-if="mostrarTop" :resultados="results"/>

</template>

<script>
import Block from './components/Block.vue'
import Mensaje from './components/Mensaje.vue'
import Top from './components/Top.vue'

export default {
  name: 'App',
  data(){
    return{
      playing: false,
      mostrarMensaje: false,
      mostrarTop: false,
      delay: null,
      score: null,
      results: [],
    }
  },
  components: {
    Block,
    Mensaje,
    Top,
  },
  methods:{
    start(){
      this.delay = 1500 + Math.random() * 5000;
      this.playing = true;
      this.mostrarMensaje = false;
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.playing = false;
      this.mostrarMensaje = true;
      this.actualizarTop();
    },
    actualizarTop(){
      this.results.push(this.score)
      this.results.sort(function(a, b){return a-b});
      this.mostrarTop = true;
    },
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
