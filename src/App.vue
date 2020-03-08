<template>

  <div id="app">
    <WeatherBlock :weatherData="current" :forecast="forecast" />
  </div>

</template>

<script>

  import WeatherBlock from './components/WeatherBlock.vue'

  export default {
    name: 'App',
    components: {
      WeatherBlock
    },
    data() {
      return {
        current: {},
        forecast: {}
      }
    },
    created() {
      const location = 'Amersfoort',
        unit = 'metric',
        key = '96d79d8f8922b949d5e6b6b905e03a2a',
        base = 'http://api.openweathermap.org/data/2.5/'

      const CurrentWeather = async () => {
        const response = await fetch(base + 'weather?q=' + location + '&appid=' + key + '&units=' + unit)
        const myJson = await response.json()
        this.current = myJson
      }

      const Forecast = async () => {
        const response = await fetch(base + 'forecast?q=' + location + '&appid=' + key + '&units=metric')
        const myJson = await response.json()
        this.forecast = myJson
      }
      Forecast()
      CurrentWeather()
    }
  }

</script>

<style lang="scss">

  @import '~normalize.css';

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  *,
  ::before,
  ::after {
    box-sizing: border-box;
  }

</style>
