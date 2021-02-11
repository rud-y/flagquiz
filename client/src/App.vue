<template>
<div id="app">
  <quiz-board welcomeMsg="FunWithFlags"/>
  <flag />
  <country-name :country="firstCountryName"/>
  <country-name :country="secondCountryName"/>
  <country-name :country="thirdCountryName"/>
  <country-name :country="fourthCountryName"/>
</div>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
import QuizBoard from './components/QuizBoard.vue'
// import Flag from './components/Flag'
import CountryName from './components/CountryName'

export default {
  name: 'App',
  data() {
    return {
      countries: [],
      firstCountryName: {},
      secondCountryName: '',
      thirdCountryName: {},
      fourthCountryName: {},
      selectedCountryName: {},
      countryFlag: {},
      score: 0,
    }
  },

  mounted() {
    fetch("https://restcountries.eu/rest/v2/all")
    .then(res => res.json())
    .then(countries => this.assignRandomNames(countries))
    console.log("First country: " + this.firstCountryName);
  },

methods: {
  assignRandomNames(countriesArray) {
    let names = [];
    countriesArray.forEach(country => {
      names.push(country.name);
    })
    const first =  names[Math.floor(Math.random() * names.length)];
    this.firstCountryName = first;

    const second =  names[Math.floor(Math.random() * names.length)];
    this.secondCountryName = second;

    const third =  names[Math.floor(Math.random() * names.length)];
    this.thirdCountryName = third;

    const fourth =  names[Math.floor(Math.random() * names.length)];
    this.fourthCountryName = fourth;
    
  },


},
  components: {
    'quiz-board': QuizBoard,
    // 'flag': Flag,
    'country-name': CountryName
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
  margin-top: 45px;
}
</style>
