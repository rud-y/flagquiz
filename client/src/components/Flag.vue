<template>
  <div>
    <img class="flag-image" v-bind:src="getImageUrl(image)" alt="a flag image"/>
  </div>
</template>

<script>
export default {
  name: 'flag',
  props: ['image'],

  methods: {
    getImageUrl(flag) {
      return flag;
    }
  }
}

</script>

<style scoped>
  .flag-image{
    width: 30%;
    padding: 1rem;
  }

</style>
