<template>
  <h1>Reaction timer!!</h1>
  <button v-if="isPlaying === false" @click="start">Start</button>
  <Block v-if="isPlaying === true" :delay="delay" @end="endGame"/>
  <Results v-if ="showResults" :score ="score"/>
  <!-- <p v-if="showResults">Reaction time: {{score}} ms</p> -->
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: {
    Block, Results
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start(){
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000 
      this.showResults = false;
    },
    endGame(reactionTime){ //RECEIVES the data from block.vue
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
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
  color: #2c3e50;
  margin-top: 60px;
}

button {
  background: turquoise;
  color:white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
</style>
