<template>
  <dialog ref="dialog">
    <div class="dialog-content">
      <p>{{ winnerRef }} is the winner!</p>
    </div>
  </dialog>
</template>

<script setup>
import { ref, toRef, defineProps, watch } from 'vue'

const props = defineProps({
  winner: {
    type: String,
    default: undefined,
  },
})

const winnerRef = toRef(props, 'winner')

const dialog = ref()

watch(winnerRef, (newValue, oldValue) => {
  console.log(newValue, oldValue)
  if (newValue !== undefined && oldValue === undefined) {
    console.log(winnerRef)
    dialog.value.showModal()
  }
})
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
