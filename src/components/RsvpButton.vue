<script setup lang="ts">
import { useRouter } from 'vue-router'

const router = useRouter()

function goToRsvp() {
  router.push('/rsvp')
}
</script>

<template>
  <button class="rsvp-button" @click="goToRsvp">RSVP</button>
</template>

<style scoped>
.rsvp-button {
  display: inline-block;
  padding: 16px 48px;
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 1.2rem;
  letter-spacing: 0.15em;
  color: #fff;
  background-color: #c9a87c;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition:
    background-color 0.3s ease,
    transform 0.2s ease;
}

.rsvp-button:hover {
  background-color: #b8956a;
  transform: translateY(-2px);
}

.rsvp-button:active {
  transform: translateY(0);
}
</style>
