<template>
  <h1>Counter</h1>
  <h2>{{ count }}</h2>
  <div>
    <button>Decrease</button><button>Reset</button><button>Increase</button>
  </div>
</template>

<script setup>
let count = 0
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
