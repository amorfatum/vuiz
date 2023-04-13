<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Counter from './components/Counter.vue'
import Questions from './components/Questions.vue'
</script>

<template>
  <header>
   <!--<img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />-->
  </header>
  <RouterView />
</template>

<style scoped>
header{
  width: 100%;
  position: absolute;
  top: 0;
  height: 10px;
}
</style>
