<template>
  <img alt="Ninja Logo" src="./assets/Ninja-Logo.png"/>
  <h1> Ninja Reaction Timer </h1>
  <button @click="start" :disabled="isPlaying"><b> Play! </b></button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start() {
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000 /* this means a random time between 2000 milliseconds (2s) up to 7000 (7s).  */
      this.showResult = false
    },
    endGame(reactTime) {
      this.score = reactTime
      this.isPlaying = false
      this.showResult = true
    }
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
img {
  height: 90px;
  }
button {
  background: rgba(5, 2, 24, 0.849);
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button:hover {
  background: rgba(16, 55, 182, 0.849)
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
