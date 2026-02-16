<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <div class="app">
    <RouterView />
  </div>
</template>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Georgia', 'Times New Roman', serif;
  background-color: #fdf6f0;
  color: #4a3728;
  min-height: 100vh;
}

.app {
  min-height: 100vh;
}
</style>
