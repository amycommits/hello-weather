<template>
  <view class="app">
    <Now :location="weather.location" :now="weather.now"/>
    <Hourly :hourly="weather.hourly" />
    <Future :forecast="weather.forecast" />
    <view class="user-options">
      <textInput
        v-if="isClicked"
        class="weather-input"
        v-model="weather.now.weather"
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
 import Now from './components/Now'
 import Hourly from './components/Hourly'
 import Future from './components/Future'

 export default {
   name: 'app-entry',
   components: { Ionicons, Now, Hourly, Future },
   data() {
     return {
       isClicked: false,
       weather: json,
       fromApi: null
     }
   },
   methods: {
     handleClick () {
       this.isClicked = !this.isClicked
     },
     fahrenheitFormula(kelvin) {
      return Math.round(1.8 * (kelvin - 273.15) + 32)
     }
   },
   mounted: function () {
     const apiKey = 'b6907d289e10d714a6e88b30761fae22' //your api key
       const weatherLink = `https://samples.openweathermap.org/data/2.5/weather?zip=94040,us&appid=${apiKey}`
     
       fetch(weatherLink)
        .then(response => response.json())
        .then(data => 
          { 
            this.fromApi = data
            this.weather.now.weather = this.fromApi.weather[0].description
            this.weather.now.temp = this.fahrenheitFormula(this.fromApi.main.temp)
          }
        )
   }
 }
 </script>
<style>
.app {
  background-color: lightskyblue;
}

.weather-input {
  background-color: lightgray;
}
</style>
