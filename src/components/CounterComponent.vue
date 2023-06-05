<template>
  <div class="section-counters">
    <div id="counters" v-for="(counter, index) in counters" :key="index">
      <h1>Counter {{ index + 1 }}</h1>
      <h2>{{ counter }}</h2>
      <div class="buttons">
        <button @click="decrement(index)">Decrease</button>
        <button @click="reset(index)">Reset</button>
        <button @click="increment(index)">Increase</button>
      </div>
      <button class="delete" v-show="counters.length > 1" @click="deleteCounter(index)">Delete counter</button>
    </div>
    <button class="add-counter" @click="newCounter">Add Counter</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

let counters = ref([0])

console.log(counters)

function increment(i) {
  counters.value[i]++;
}
function decrement(i) {
  counters.value[i]--
}
function reset(i) {
  counters.value[i] = 0
}
function newCounter() {
  counters.value.push(0)
}
function deleteCounter(i) {
  counters.value.splice(i, 1)
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.section-counters {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

#counters {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 0.5rem;
}

h1 {
  font-family: Roboto-Bold;
  color: darkblue;
  font-size: 1.5rem;
  line-height: 1em;
}

h2 {
  color: darkgreen;
  font-size: 3rem;
  font-family: Roboto-Black;
  line-height: 1em;
}

.buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
}



.add-counter {
  width: 100%;
  background: darkgreen;
  border-color: darkgreen;
  color: white;
}

.delete {
  width: 100%;
  background: darkred;
  color: white;
  border-color: darkred;
}
</style>
