<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="startPlay" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @endGame="endGame"/>
  <!-- <p v-if="showResults">Reaction Time: {{ reactionTime }} ms</p> -->
  <Results v-if="showResults" :reactionTime="reactionTime"/>
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: null,
      showResults: false
    }
  },
  methods: {
    startPlay() {
      this.isPlaying = true
      this.delay = 2000 + Math.random()*5000
      this.showResults = false
      //console.log(this.delay)
    },
    endGame(reactionTime) {
      this.reactionTime = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  },
  components: {
    Block, Results
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
