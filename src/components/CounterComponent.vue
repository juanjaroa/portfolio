<template>
  <h1>Counter</h1>
  <h2>{{ count }}</h2>
  <div>
    <button @click="decrement">Decrease</button>
    <button @click="reset">Reset</button>
    <button @click="increment">Increase</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

let count = ref(0)
console.log(count)
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
h1{
  font-family: Roboto-Bold;
  color: darkslateblue;
}
h2{
  color: darkgreen;
  font-size: 2rem;
}
</style>
