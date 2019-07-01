<template>
  <view class="container">
    <text>{{ location }}</text>
    <text>{{ now['weather'] }}</text>
    <text>{{ now['temp'] }}</text>
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
