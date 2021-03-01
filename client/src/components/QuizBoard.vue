<template>
  <div class="intro-page wrapper">
    <h1 class="item">Fun with flags</h1>
    <h3 class="item" id="intro">Let's check your flags knowledge </h3>
    <button class="start-btn item" v-on:click="startQuiz">Start</button> 
  </div>
</template>

<script>
import { eventBus } from '@/main.js'
export default {
  name: 'quiz-board',

  // props: {
  //   title: String,
  //   intro: String
  //   },
  

  methods: {
    startQuiz() {
      eventBus.$emit('start-quiz');
      console.log("eventbus emitted ___");
    }
  }
}
  

</script>

<style scoped>
.intro-page {
  background-color: #f1f1f8;
}
.wrapper {
  display: flex;
  flex-flow: column wrap;
  justify-content: center;
  align-items: center;
}
.item {

}

h1 {
  text-align: center;
  font-size: 20px;
  color: rgb(6, 104, 134);
}

#intro {
  text-align: center;
  box-shadow: 2px 4px 16px #aaaaaa;
  max-width: 18rem;
  margin: 0 auto;
  padding: 0.3rem;

}
.start-btn {
  display: block;
  margin: 0 auto;
  margin-top: 2rem;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
