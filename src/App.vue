<template>
  <CounterComponent />
</template>

<script setup>
import CounterComponent from './components/CounterComponent.vue'
</script>

<style>
@font-face {
  font-family: 'Roboto';
  src: url(./fonts/Roboto-Regular.ttf) format('truetype');
}
@font-face {
  font-family: 'Roboto-Bold';
  src: url(./fonts/Roboto-Bold.ttf) format('truetype');
}
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>