<template>
  <CounterComponent v-show="showCounterComponent" />
  <TriquiComponent v-show="showTriquiComponent" />
</template>

<script setup>
import CounterComponent from './components/CounterComponent.vue'
import TriquiComponent from './components/TriquiComponent/TriquiComponent.vue'

let showCounterComponent = true
let showTriquiComponent = false
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

@font-face {
  font-family: 'Roboto-Medium';
  src: url(./fonts/Roboto-Medium.ttf) format('truetype');
}

@font-face {
  font-family: 'Roboto-Black';
  src: url(./fonts/Roboto-Black.ttf) format('truetype');
}

#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 1rem;
  color: #2c3e50;
  padding: 3rem;

}

button,
#triqui-grid .cell {
  user-select: none;
}

button {
  padding: 0.25rem 1rem;
  border: solid 2px;
  border-radius: 0.25rem;
  cursor: pointer;
  font-size: 0.75rem;
  font-family: Roboto-Medium;
  text-align: center;
}
</style>