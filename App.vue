<template>
  <view class="app">
    <view class="now-container">
      <text>{{ location }}</text>
      <text>{{ now['weather'] }}</text>
      <text>{{ now['temp'] }}</text>
    </view>
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
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
</style>
