<template>
<div id="countdown-wrapper">
  Remaining: <span id="time-remaining">{{remainingTime}}</span>
</div>
</template>

<script>
// import {eventBus} from '@/main.js'

export default {
  data() {
    return {
      limit: 10,
      remainingTime: null
    }
    },

  methods: {
    roundCountdown() {
      const timer = setInterval(() => {
        this.remainingTime -= 1;
          if(this.remainingTime === 0) {
            clearInterval(timer);
            // eventBus.$emit('time-over');
          }

      }, 1000);
    }
  },

   mounted() {
     this.remainingTime = this.limit;
     this.roundCountdown();
    },
    
}
</script>

<style scoped>
  #countdown-wrapper {
    max-width: 7rem;
    background-color: whitesmoke;
    border: solid 2px black;
  }

</style>