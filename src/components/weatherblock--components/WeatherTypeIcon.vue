<template>

  <img :src="'http://openweathermap.org/img/wn/' + icon + '@2x.png'" :alt="text">

</template>

<script>

  export default {
    name: 'WeatherTypeIcon',
    props: {
      icon: String,
      text: String
    }
  }

</script>

<style scoped lang="scss">
  img{
    max-width: 100%;
  }
</style>
