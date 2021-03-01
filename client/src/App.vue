<template>
<div id="app">
  <quiz-board v-if="componentDisplay === 'quiz-board'" />
  <play-board v-if="componentDisplay === 'play-board'" />
</div>
</template>

<script>
import { eventBus } from '@/main.js'
import QuizBoard from './components/QuizBoard.vue'
import PlayBoard from './components/PlayBoard.vue'

export default {
  name: 'App',
  data() {
    return {
      score: 0,
      componentDisplay: 'quiz-board'
    }
  },

  components: {
    'quiz-board': QuizBoard,
    'play-board': PlayBoard
  },

  mounted() {
    eventBus.$on('start-quiz',function() {
      console.log("Quiz starting _ _ _");
      this.componentDisplay = "play-board";
    });

    // eventBus.$on('time-up', () => {
    //   console.log("End of the quiz _ _ _")
    // });

  },

}
</script>


<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 45px;
}
.container {
  border: solid 1px darkblue;
  background-color: rgb(237, 245, 191);
}
.disabled {
  background-color: darkgray;
  color: rgb(150, 142, 142);
}
</style>
