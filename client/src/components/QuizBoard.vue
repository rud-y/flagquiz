<template>
  <div class="hello">
    <h1>Hi</h1>
  </div>
</template>

<script>
export default {
  name: 'quiz-board',

  props: {
    welcomeMsg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  margin: 0 auto;
  font-size: 20px;
  color: rgb(153, 12, 153);
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
