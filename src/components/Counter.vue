<script>
import { ref, reactive } from 'vue'

const count = ref(0)

export const incCount = () => {
  count.value++;
}

export const decCount = () => {
  count.value--;
}

export default {
  setup(){
    return {
      count
    }
  }
}
</script>

<template>
<div id="app" class="counter">
  <span>Count is: {{ count }}</span>
</div>
</template>

<style scoped>
.counter{
  top: 50%;
  left: 25%;
  color: white;
  font-size: large;
}
</style>
