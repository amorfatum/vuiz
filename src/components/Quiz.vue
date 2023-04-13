<template>
    <div>
      <Questions />
      <Counter />
    </div>
  </template>
  
  <script>
  import Questions from '../components/Questions.vue'
  import Counter from '../components/Counter.vue'
  
  export default {
    name: 'Quiz',
    components: {
      Questions,
      Counter
    }
  }
  </script>