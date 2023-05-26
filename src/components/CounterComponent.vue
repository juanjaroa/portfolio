<template>
  <h1>Counter</h1>
  <h2>{{ count }}</h2>
  <div class="buttons">
    <button @click="decrement">Decrease</button>
    <button @click="reset">Reset</button>
    <button @click="increment">Increase</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

let count = ref(0)

function increment() {
  count.value++;
}
function decrement() {
  count.value--
}
function reset() {
  count.value = 0
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  font-family: Roboto-Bold;
  color: darkblue;
  font-size: 2rem;
}

h2 {
  color: darkgreen;
  font-size: 4rem;
  font-family: Roboto-Medium;
}

.buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}

button {
  padding: 0.25rem 1rem;
  border: solid 2px;
  border-radius: 0.25rem;
  cursor: pointer;
  font-size: 0.75rem;
  font-family: Roboto-Medium;
}
</style>
