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
        <p class="detail-item">MAY 9TH, 2026</p>
        <p class="detail-item">
          <a
            href="https://www.google.com/maps/place/All+Grand+Events+%2B+Floral/data=!4m2!3m1!1s0x0:0x593a3e5256c6f337?sa=X&ved=1t:2428&ictx=111"
            target="_blank"
            rel="noopener noreferrer"
            class="location-link"
            >2233 W GRAND RIVER AVE, OKEMOS, MI 48864</a
          >
        </p>
      </div>
      <div class="cta">
        <RsvpButton />
      </div>
      <div class="registry">
        <a
          href="https://www.amazon.com/baby-reg/hannahandcap-wilson-june-2026-muskegon/2MCLTPZ8AVFP7"
          target="_blank"
          rel="noopener noreferrer"
          class="registry-link"
          >BABY REGISTRY</a
        >
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

.location-link {
  color: #a08060;
  text-decoration: none;
  border: 2px solid #c9a87c;
  border-radius: 25px;
  padding: 0.25rem 0.75rem;
  transition:
    background-color 0.2s,
    color 0.2s;
}

.location-link:hover {
  background-color: #c9a87c;
  color: #fff;
}

.cta {
  margin-top: 1rem;
}

.registry {
  margin-top: 1.5rem;
}

.registry-link {
  display: inline-block;
  padding: 10px 32px;
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 1.1rem;
  letter-spacing: 0.15em;
  color: #fff;
  background-color: #c9a87c;
  border: none;
  border-radius: 25px;
  text-decoration: none;
  cursor: pointer;
  transition:
    background-color 0.3s ease,
    transform 0.2s ease;
}

.registry-link:hover {
  background-color: #b8956a;
  transform: translateY(-2px);
}

.registry-link:active {
  transform: translateY(0);
}

@media (max-width: 600px) {
  .title {
    font-size: 2rem;
  }
}
</style>
