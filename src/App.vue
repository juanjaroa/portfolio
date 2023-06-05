<template>
  <nav>
    <p>JRoa's Portfolio</p>
    <ul>
      <li @click="pickCounter">Counter</li>
      <li @click="pickTriqui">Triqui</li>
    </ul>
  </nav>
  <CounterComponent v-show="showCounterComponent" />
  <TriquiComponent v-show="showTriquiComponent" />
</template>

<script setup>
import { ref } from 'vue'
import CounterComponent from './components/CounterComponent.vue'
import TriquiComponent from './components/TriquiComponent/TriquiComponent.vue'

let showCounterComponent = ref(false)
let showTriquiComponent = ref(true)

function pickCounter() {
  showCounterComponent.value = true
  showTriquiComponent.value = false
}
function pickTriqui() {
  showCounterComponent.value = false
  showTriquiComponent.value = true
}
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
  padding: 6rem 3rem;

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

nav {
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  border-bottom: 0.5px solid rgba(0, 0, 0, 0.25);
  background: white;
}

nav ul {
  display: flex;
  gap: 1rem;
}

nav ul li {
  cursor: pointer;
}
</style>