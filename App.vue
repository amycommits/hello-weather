<template>
  <view class="app">
    <view class="now-container">
      <text>{{ location }}</text>
      <text>{{ now['weather'] }}</text>
      <text>{{ now['temp'] }}</text>
    </view>
    <scroll-view class="future-weather-container">
      <view class="future-day" v-for="(day, key, index) in forecast" :key="key">
        <text> {{ key }} </text>
        <text> {{ day['weather'] }} </text>
        <text> {{ day['temp-high'] }} </text>
        <text> {{ day['temp-low'] }} </text>
      </view>
    </scroll-view>
  </view>
</template>
 <script>
 export default {
   name: 'app-entry',
   data() {
     return {
       location: 'Washington, DC',
       now: {
         temp: 97,
         weather: 'cloudy'
       },
       forecast: {
         '2019-07-25': {
           'temp-high': 96,
           'temp-low': 85,
           'weather': 'rainy'
         },
         '2019-07-26': {
           'temp-high': 98,
           'temp-low': 88,
           'weather': 'rainy'
         },
         '2019-07-27': {
           'temp-high': 92,
           'temp-low': 72,
           'weather': 'sunny'
         },
         '2019-07-28': {
           'temp-high': 87,
           'temp-low': 77,
           'weather': 'cloudy'
         },
         '2019-07-29': {
           'temp-high': 95,
           'temp-low': 83,
           'weather': 'cloudy'
         }
       }
     }
   }
 }
 </script>
<style>
.app {
  background-color: lightskyblue;
}
.now-container {
  align-items: center;
  justify-content: center;
  padding: 50;
}
.future-weather-container {
  height: 100;
}
.future-day {
  flex: 1;
  flex-direction: row;
}
</style>
