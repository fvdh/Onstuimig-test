<template>

  <ul class="forecast-list">
    <li v-for="(item, x) in forecast" :key="x" class="forecast-list-item">
      <span class="date">{{ item.dt_txt.substring(0, item.dt_txt.length-3).split(' ')[0].split('-').reverse().join('-')}}</span>
      <span class="time">{{ item.dt_txt.substring(0, item.dt_txt.length-3).split(' ')[1] }}</span>

      <WeatherTypeIcon :icon="item.weather[0].icon" :text="item.weather[0].description" />

      <span class="temp">{{Number((item.main.temp).toFixed(0))}}°</span>

    </li>
  </ul>

</template>

<script>
import WeatherTypeIcon from '@/components/weatherblock--components/WeatherTypeIcon.vue'

  export default {
    name: 'Forecast',
    components: {
      WeatherTypeIcon
    },
    props: {
      forecast: Array
    }
  }

</script>

<style scoped lang="scss">

  .forecast-list{
    list-style: none;
    text-align: left;
    padding: 0;
    margin: 40px 0 0 0;
    display: grid;
    grid-template-columns: repeat( auto-fit, minmax(100px, 1fr) );
    .forecast-list-item{
      text-align: center;
      padding: 10px;
      border-radius: 3px;
      transition: background .2s, transform .2s;
      .time, .date, .temp{
        display: block;
      }
      .time{
        margin-bottom: -5px;
        font-size: 14px;
      }
      .date{
        font-size: 10px;
        opacity: .7;
        margin-bottom: 2px;
        font-weight: 300;
        letter-spacing: 0.05em;
      }
      .temp{
        margin: -8px 0 8px 0;
        font-weight: bold;
        font-size: 14px;
      }
      img{
        max-width: 60%;
      }

      &:hover{
        background: rgba(255,255,255,.8);
        color: #000;
        transform: scale(1.2);
      }
    }
  }

</style>
