<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const count = ref(0)


const incCount = () => {
    count.value++;
}

const decCount = () => {
    count.value--;
}
</script>

<template>
<div id="app" class="counter">
  <span>Count is: {{ count }}</span>
  <div>
    <button @click="count++">
      Increment
    </button>
    <button @click="count--">
      Decrement
    </button>
  </div>
</div>
</template>

<style scoped>
.counter{
    top: 50vh;
}

</style>
