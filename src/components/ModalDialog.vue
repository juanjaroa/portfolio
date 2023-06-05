<template>
  <dialog ref="dialog">
    <div class="dialog-content">
      <img :src="winnerRef === 'x' ? '/assets/x.png' : '/assets/o.png'" alt="">
      <p>WINNER!</p>
      <button @click="emitModalClosed">Ok!</button>
    </div>
  </dialog>
</template>

<script setup>
import { ref, toRef, defineProps, defineEmits, watch } from 'vue'

//props recibidas
const props = defineProps({
  winner: {
    type: String,
    default: undefined,
  },
})

//evento emitido
const emit = defineEmits(['modalClosed'])

const winnerRef = toRef(props, 'winner')

const dialog = ref()

const emitModalClosed = () => {
  emit('modalClosed')
  dialog.value.close()
}

watch(winnerRef, (newValue, oldValue) => {
  if (newValue !== undefined && oldValue === undefined) {
    dialog.value.showModal()
  }
})
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
dialog::backdrop {
  background: rgba(0, 0, 0, 0.5);
}

dialog {
  border: none;
  padding: 2rem;
}

.dialog-content {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 1rem
}

p {
  font-size: 2rem;
  font-family: Roboto-Black;
}
</style>
