<template>
  <view class="app">
    <view class="now-container">
      <text>{{ weather.location }}</text>
      <text>{{ weather.now['weather'] }}</text>
      <view class="current-temp">
        <text>{{ weather.now['temp'] }}</text>
        <image
          class="degree-icon"
          :source="require('./assets/degree_icon.jpg')" />
      </view>
    </view>
    <scroll-view horizontal class="hourly-weather-container">
      <view class="this-hour" 
        v-for="(hour, key, index) in weather.hourly"
        :key="key">
        <text> {{ key }} </text>
        <Ionicons
          :name="getWeatherIcon(hour.weather)"
          class="weather-icon"
        />
        <text> {{ hour.temp }} </text>
      </view>
    </scroll-view>
    <scroll-view class="future-weather-container">
      <view class="future-day" v-for="(day, key, index) in weather.forecast" :key="key">
        <text> {{ key }} </text>
        <Ionicons
          :name="getWeatherIcon(day.weather)"
          class="weather-icon"
        />
        <text> {{ day['temp-high'] }} </text>
        <text> {{ day['temp-low'] }} </text>
      </view>
    </scroll-view>
    <view class="user-options">
      <textInput
        v-if="isClicked"
        class="weather-input"
        v-model="now.weather"
      />
      <button
        :on-press="handleClick"
        :title="isClicked ? '-' : '+'"
      />
    </view>
  </view>
</template>
 <script>
 import { Ionicons } from "@expo/vector-icons";
 import json from './data/weather.json'
 export default {
   name: 'app-entry',
   components: { Ionicons },
   data() {
     return {
       isClicked: false,
       weather: json
     }
   },
   methods: {
     handleClick () {
       this.isClicked = !this.isClicked
     },
     getWeatherIcon(name) {
       switch(name) {
         case 'cloudy':
           return "md-cloud-outline"
           break;
          case 'thunderstorm':
            return "md-thunderstorm"
            break;
          case 'rainy':
            return "md-rainy"
            break;
          case 'partly-cloudy':
            return 'md-partly-sunny'
            break;
          case 'sunny':
            return "md-sunny"
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
  font-size: 25px;
}
.hourly-weather-container {
  height: 100;
}
.this-hour {
  flex: 1;
  flex-direction: column;
  padding-left: 150;
}
.weather-input {
  background-color: lightgray;
}
</style>
