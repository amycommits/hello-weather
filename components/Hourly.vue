<template>
  <scroll-view horizontal class="hourly-weather-container">
    <view class="this-hour" 
      v-for="(hour, key, index) in hourly"
      :key="key">
      <text> {{ key }} </text>
      <Ionicons
        :name="getWeatherIcon(hour.weather)"
        class="weather-icon"
      />
      <text> {{ hour.temp }} </text>
    </view>
  </scroll-view>
</template>
<script>
  import { Ionicons } from "@expo/vector-icons";
  export default {
    name: 'hourly',
    components: { Ionicons },
    props: ['hourly'],
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
.hourly-weather-container {
  height: 100;
}
.this-hour {
  flex: 1;
  flex-direction: column;
  padding-left: 150;
}
.weather-icon {
  font-size: 25px;
}
</style>