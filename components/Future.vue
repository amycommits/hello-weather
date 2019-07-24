<template>
  <scroll-view class="future-weather-container">
    <view class="future-day" v-for="(day, key, index) in forecast" :key="key">
      <text> {{ key }} </text>
      <Ionicons
        :name="getWeatherIcon(day.weather)"
        class="weather-icon"
      />
      <text> {{ day['temp-high'] }} </text>
      <text> {{ day['temp-low'] }} </text>
    </view>
  </scroll-view>
</template>
<script>
import { Ionicons } from "@expo/vector-icons";

export default {
  name: 'future',
  components: { Ionicons },
  props: ['forecast'],
  methods: {
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
<style scoped>
.future-weather-container {
  height: 100;
}
.future-day {
  flex: 1;
  flex-direction: row;
}
.weather-icon {
  font-size: 25px;
}
</style>
