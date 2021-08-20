<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="startPlay" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" />
</template>

<script>
import Block from "./components/Block.vue"

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null
    }
  },
  methods: {
    startPlay() {
      this.isPlaying = true
      this.delay = 2000 + Math.random()*5000
      //console.log(this.delay)
    }
  },
  components: {
    Block
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
