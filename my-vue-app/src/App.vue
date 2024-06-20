<template>
  <div>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">play</button>
    <blockButton v-if="isPlaying" :delay="delay" @end="endGame"/>
    <resultTime v-if="showResults" :score="score" />
  </div>
 
</template>

<script>

import blockButton from './components/blockButton.vue'
import resultTime from './components/resultTime.vue'

export default {
  name: 'App',
  components: { blockButton, resultTime }, 

  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true
      this.showResults = false

    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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

button {
  background: lightblue;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}

h1 {
  color: rgb(241, 150, 165);
}
</style>
