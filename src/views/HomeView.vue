<script setup lang="ts">
import RsvpButton from '@/components/RsvpButton.vue'
</script>

<template>
  <main class="home">
    <div class="content">
      <p class="preheading">You're Invited to</p>
      <h1 class="title">Hannah &amp; Cap's<br />Baby Shower</h1>
      <div class="divider">&#10045;</div>
      <div class="details">
        <p class="detail-item">Date TBD</p>
        <p class="detail-item">Location TBD</p>
      </div>
      <div class="cta">
        <RsvpButton />
      </div>
    </div>
  </main>
</template>

<style scoped>
.home {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  padding: 2rem;
  text-align: center;
}

.content {
  max-width: 600px;
}

.preheading {
  font-size: 1rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: #a08060;
  margin-bottom: 0.75rem;
}

.title {
  font-size: 2.8rem;
  font-weight: 400;
  line-height: 1.3;
  color: #4a3728;
  margin-bottom: 1.5rem;
}

.divider {
  font-size: 1.5rem;
  color: #c9a87c;
  margin-bottom: 1.5rem;
}

.details {
  margin-bottom: 2.5rem;
}

.detail-item {
  font-size: 1.1rem;
  line-height: 2;
  color: #6b5744;
}

.cta {
  margin-top: 1rem;
}

@media (max-width: 600px) {
  .title {
    font-size: 2rem;
  }
}
</style>
