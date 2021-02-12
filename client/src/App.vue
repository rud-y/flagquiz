<template>
<div id="app">
  <div class="container">
  <quiz-board welcomeMsg="FunWithFlags"/>
  <button v-on:click="assignRandomNamesAndFlag">Start</button> 

  <flag :image="countryFlag"/>
  <country-name :country="firstCountryName"/>
  <country-name :country="secondCountryName"/>
  <country-name :country="thirdCountryName"/>
  <country-name :country="fourthCountryName"/>
  </div>
</div>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
import QuizBoard from './components/QuizBoard.vue'
import Flag from './components/Flag'
import CountryName from './components/CountryName'

export default {
  name: 'App',
  data() {
    return {
      countries: [],
      firstCountryName: '',
      secondCountryName: '',
      thirdCountryName: {},
      fourthCountryName: {},
      countryFlag: {},
      score: 0,
    }
  },

  mounted() {
    fetch("https://restcountries.eu/rest/v2/all")
    .then(response => response.json())
    .then(data => this.countries = data)
    .then(countries => console.log(countries))
  },

methods: {
  assignRandomNamesAndFlag: function() {
    const first =  this.countries[Math.floor(Math.random() * this.countries.length)];
    // console.log(first);
    this.firstCountryName = first.name;

    const second =  this.countries[Math.floor(Math.random() * this.countries.length)];
    this.secondCountryName = second.name;

    const third =  this.countries[Math.floor(Math.random() * this.countries.length)];
    this.thirdCountryName = third.name;

    const fourth =  this.countries[Math.floor(Math.random() * this.countries.length)];
    this.fourthCountryName = fourth.name;

    const selected = [
      first,
      second,
      third,
      fourth
    ];
    
    const oneCountry = selected[Math.floor(Math.random() * selected.length)];
    this.countryFlag = oneCountry.flag;
  }
    // console.log(this.countryFlag);


    //condition to match one of the countries
    // const selectedFlags = countriesArray.filter(country => {
    //   let selected = [];

    //     if (country.name === this.firstCountryName
    //     && country.name === this.secondCountryName
    //     && country.name === this.thirdCountryName
    //     && country.name === this.fourthCountryName) {
    //       selected.push(country);
    //     }
      
    //   return selected;
      
    // })
    // console.log(selectedFlags);
    // const flagImg = selectedFlags[Math.floor(Math.random() * selectedFlags.length)];
    // this.countryFlag = flagImg;
  

  // assignFlagImage(array) {
  //   let flags = [];
  //   array.forEach(country => {
  //     flags.push(country.flag);
  //   })
  // }

},
  components: {
    'quiz-board': QuizBoard,
    'flag': Flag,
    'country-name': CountryName
  }
}
</script>


<style scoped>
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 45px; */
}
.container {
  border: solid 1px darkblue;
  background-color: rgb(225, 236, 247);
}
</style>
