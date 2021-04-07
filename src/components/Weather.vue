<template>
  <div class="weather-box">
    <div class="img-box">
      <img :src="'./src/assets/'+ weatherData.wea_img + '.png'" />
    </div>
    <div>{{weatherData.date}}</div>
    <div>{{weatherData.wea}}</div>
    <div>{{weatherData.tem_night}}~{{weatherData.tem_day}} ℃</div>
    <div>{{weatherData.win}} {{weatherData.win_speed}}</div>
  </div>
</template>

<script>
export default {
  name: 'Weather',
  props: {
    weatherData: Object
  },
  data() {
    return {
    }
  }
}
</script>

<style scoped>
.weather-box{
  width: 200px;
  margin: 10px;
  padding: 20px;
  /* border: 1px solid #002FA7; */
  border-radius: 5px;
  background-color: white;
  box-shadow: 0 8px 12px #ebedf0;
  line-height: 24px;
  font-weight: bold;
  
}
.img-box{
  /* width: 180px; */
  height: 180px;
  background-color: #002FA7;
  text-align: center;

}
img{
  /* margin-top: 20px; */
  width: 100px;
  margin-top: 40px;
  /* line-height: 180px; */
}
</style>
