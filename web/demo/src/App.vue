<template>
  <div>
    <div style="font-weight:bold;font-size:30px">{{city}}一周天气</div>
    <div class="week-weather">
      <Weather v-for="weatherData in weatherList" :weatherData="weatherData" :key="weatherData.date"></Weather>
    </div>
    <div style="font-weight:bold;font-size:30px">TODOS</div>
    <Todos></Todos>
  </div>
</template>

<script>
import Weather from './components/Weather.vue'
import Todos from './components/Todos.vue'

export default {
  name: 'App',
  components: {
    Weather,
    Todos
  },
  data () {
    return {
      city: '',
      weatherList: []
    }
  },
  created () {
    // 接口返回数据结构
    // {
    //   "cityid": "101210101",
    //   "city": "杭州",
    //   "update_time": "2021-04-07 11:39:01",
    //   "data": [
    //     {
    //       "date": "2021-04-07",
    //       "wea": "小雨",
    //       "wea_img": "yu",
    //       "tem_day": "14",
    //       "tem_night": "10",
    //       "win": "东北风",
    //       "win_speed": "3-4级"
    //     }
    //   ]
    // }
    fetch('https://www.tianqiapi.com/free/week?appid=68852321&appsecret=BgGLDVc7')
      .then((response) => {
        let weatherInfo = response.json()
        return weatherInfo
      })
      .then((info) => {
        this.city = info.city
        this.weatherList = info.data
      })
  }
}
</script>
<style>
.week-weather {
  display: flex;
  /* align-items: center; */
  justify-content: space-between;
}
</style>