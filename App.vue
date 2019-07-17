<template>
  <view class="app">
    <view class="now-container">
      <text>{{ location }}</text>
      <text>{{ now['weather'] }}</text>
      <view class="current-temp">
        <text>{{ now['temp'] }}</text>
        <image
          class="degree-icon"
          :source="require('./assets/degree_icon.jpg')" />
      </view>
    </view>
    <scroll-view class="future-weather-container">
      <view class="future-day" v-for="(day, key, index) in forecast" :key="key">
        <text> {{ key }} </text>
        <Ionicons name="md-cloud-outline" class="weather-icon" />
        <text> {{ day['temp-high'] }} </text>
        <text> {{ day['temp-low'] }} </text>
      </view>
    </scroll-view>
  </view>
</template>
 <script>
 import { Ionicons } from "@expo/vector-icons";

 export default {
   name: 'app-entry',
   components: { Ionicons },
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
   },
   methods: {
     getWeatherIcon(name) {
       switch(name) {
         case 'cloudy':
           return "md-cloud-outline"
           break;
         default:
           return "md-infinite"
           break;
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
.current-temp {
  align-items: flex-start;
  flex: 1;
  flex-direction: row;
}
.degree-icon {
  width: 10;
  height:10;
}
.weather-icon {
  font-size: 200px;
}
</style>
