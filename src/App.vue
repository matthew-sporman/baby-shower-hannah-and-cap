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

html, body {
  position: fixed;
  inset: 0;
  overflow: hidden;
}

body {
  font-family: 'Georgia', 'Times New Roman', serif;
  background-color: #fdf6f0;
  color: #4a3728;
}

.app {
  height: 100%;
}

input,
select,
textarea,
button {
  border-radius: 25px;
}

</style>
