<template>
  <view class="now-container">
    <text>{{ location }}</text>
    <text>{{ now['weather'] }}</text>
    <view class="current-temp">
    <text>{{ now['temp'] }}</text>
      <image
        class="degree-icon"
        :source="require('../assets/degree_icon.jpg')" />
    </view>
  </view>
</template>
<script>
  export default {
    name: 'now',
    props: ['location','now']
  }
</script>
<style scoped>
.now-container {
  align-items: center;
  justify-content: center;
  padding: 50;
}
.degree-icon {
  width: 10;
  height:10;
}
.current-temp {
  align-items: flex-start;
  flex: 1;
  flex-direction: row;
}
</style>