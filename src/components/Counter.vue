<script>
import { ref, onMounted, onUnmounted } from 'vue'


const count = ref(0)

export function incCount(){
    count.value++;
  }

export function decCount(){
    count.value--;
}


export default {
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
