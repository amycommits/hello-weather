<template>
  <view class="app">
    <Now :location="weather.location" :now="weather.now"/>
    <Hourly :hourly="weather.hourly" />
    <Future :forecast="weather.forecast" />
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
 import Now from './components/Now'
 import Hourly from './components/Hourly'
 import Future from './components/Future'

 export default {
   name: 'app-entry',
   components: { Ionicons, Now, Hourly, Future },
   data() {
     return {
       isClicked: false,
       weather: json
     }
   },
   methods: {
     handleClick () {
       this.isClicked = !this.isClicked
     }
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
