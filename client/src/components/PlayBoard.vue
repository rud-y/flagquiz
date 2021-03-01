<template>
    <div>
        <div class="container">
        <!-- <quiz-board welcomeMsg="FunWithFlags" intro="Let's start a flag knowledge quiz!"/> -->
        <countdown v-if="countDownOn"/>
        <flag :image="countryFlag"/>
        <country-name :country="firstCountryName"/>
        <country-name :country="secondCountryName"/>
        <country-name :country="thirdCountryName"/>
        <country-name :country="fourthCountryName"/>
  </div>
    </div>
</template>

<script>
// import { eventBus } from '@/main.js'
import Flag from './Flag.vue'
import CountryName from './CountryName.vue'
import Countdown from './Countdown.vue'
export default {
    name: 'play-board',
    data() {
        return {
            countries: [],
            firstCountryName: '',
            secondCountryName: {},
            thirdCountryName: {},
            fourthCountryName: {},
            countryFlag: {},
            selectedCountry: null,
            countDownOn: false
        }
    },


mounted() {
fetch("https://restcountries.eu/rest/v2/all")
    .then(response => response.json())
    .then(data => this.countries = data)
    // .then(countries => console.log(countries))

    // eventBus.$on('time-up');
},

components: {
    'flag': Flag,
    'country-name': CountryName,
    'countdown': Countdown
},



methods: {
    assignRandomNamesAndFlag: function() {
    this.countDownOn = true;
    const first =  this.countries[Math.floor(Math.random() * this.countries.length)];
    
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
    //choose random flag image 
    const eachCountry = selected[Math.floor(Math.random() * selected.length)];
    this.countryFlag = eachCountry.flag;
    }
}
}

</script>

<style scoped>



</style>