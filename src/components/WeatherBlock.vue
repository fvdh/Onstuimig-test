<template>

  <section class="container--weather">
    <header>
      <h1 class="temp">{{Number((weatherData.main.temp).toFixed(0))}}</h1>
      <h2 class="weather-type">{{weatherData.weather[0].description}}</h2>
      <h3 class="title">{{weatherData.name}}</h3>
    </header>
    <hr>
    <Forecast :forecast="forecast.list" />

  </section>

</template>

<script>

  import Forecast from '@/components/weatherblock--components/Forecast.vue'

  export default {
    name: 'WeatherBlock',
    components: {
      Forecast
    },
    props: {
      weatherData: Object,
      forecast: Object
    }
  }

</script>

<style scoped lang="scss">

  $breakpoint: 550px;
  header {
    padding: 40px 0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr 1fr;
    grid-gap: 0 40px;

    @media screen and (max-width: $breakpoint) {
      grid-template-columns: 1fr;
      grid-template-rows: 1fr;
    }
  }
  .container--weather {
    width: 80%;
    max-width: 800px;
    background: rgb(73, 69, 152);
    background: linear-gradient(0deg, rgba(73, 69, 152, 1) 0%, rgba(22, 171, 201, 1) 100%);

    position: absolute;
    margin: 50px 0;
    left: 50%;
    transform: translateX(-50%);
    padding: 40px;
    border-radius: 4px;
    box-shadow: 0 0 15px 10px rgba(0, 0, 0, 0.12);
    text-align: center;
    color: #fff;

    .temp {
      margin: 0;
      font-weight: 300;
      font-size: 80px;
      display: inline-block;
      width: 165px;
      height: 165px;
      background: #fff;
      color: #17aac9;
      line-height: 165px;
      border-radius: 50%;
      font-weight: bold;
      grid-row: 1 / -1;
      justify-self: end;
      position: relative;

      @media screen and (max-width: $breakpoint) {
        justify-self: center;
        margin-bottom: 30px;
      }

      &:after {
        content: 'celsius';
        position: absolute;
        left: 0;
        right: 0;
        font-size: 10px;
        font-weight: 300;
        letter-spacing: 0.05em;
        text-transform: uppercase;
        display: block;
        line-height: 1;
        bottom: 30px;
      }
    }
    .title {
      margin: 5px 0 0 0;
      text-transform: uppercase;
      letter-spacing: 0.15em;
      font-size: 12px;
      font-weight: 300;
      align-self: start;
      text-align: left;
      @media screen and (max-width: $breakpoint) {
        justify-self: center;
      }
    }
  }
  hr{
    height: 1px;
    background: #fff;
    border: none;
    opacity: .2;
  }

  .weather-type {
    margin: 0;
    color: #fff;
    letter-spacing: 0.05em;
    font-size: 12px;
    text-transform: uppercase;
    font-weight: 300;
    align-self: end;
    text-align: left;
    @media screen and (max-width: $breakpoint) {
      justify-self: center;
    }
  }

</style>
