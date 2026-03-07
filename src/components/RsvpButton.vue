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
  padding: 8px 32px;
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 0.9rem;
  letter-spacing: 0.15em;
  color: #fff;
  background-color: #c9a87c;
  border: none;
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

@media (min-aspect-ratio: 16/9) {
  .rsvp-button {
    padding: clamp(8px, 1.5vmin, 16px) clamp(24px, 4vmin, 64px);
    font-size: clamp(0.9rem, 2.2vmin, 1.8rem);
  }
}
</style>
