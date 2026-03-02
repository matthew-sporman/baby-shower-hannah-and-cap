<script setup lang="ts">
import RsvpButton from '@/components/RsvpButton.vue'
</script>

<template>
  <main class="home">
    <div class="hero-container">
      <img src="/images/background_main.png" class="hero-bg" alt="" />
      <div class="hero-overlay">
        <div class="zone-top">
          <p class="preheading">
            <span class="locally">Locally</span>
            <span class="grown">grown</span>
          </p>
        </div>
        <div class="zone-mid"></div>
        <div class="zone-bottom">
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
          <div class="buttons-row">
            <RsvpButton />
            <a
              href="https://www.amazon.com/baby-reg/hannahandcap-wilson-june-2026-muskegon/2MCLTPZ8AVFP7"
              target="_blank"
              rel="noopener noreferrer"
              class="registry-link"
              >BABY REGISTRY</a
            >
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.home {
  height: 100dvh;
  overflow: hidden;
  background: url('/images/mobile_background.png') center / cover no-repeat #b5cc8e;
  display: flex;
  justify-content: center;
  align-items: center;
}

@media (min-aspect-ratio: 16/9) {
  .home {
    background: url('/images/desktop_background.png') center / cover no-repeat;
  }

  .hero-container {
    transform: scale(0.75);
  }

}

.hero-container {
  position: relative;
  height: 100dvh;
  aspect-ratio: 3 / 4;
}

.hero-bg {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  display: grid;
  grid-template-rows: 28% 22% 1fr;
  text-align: center;
}

.zone-top {
  display: flex;
  align-items: center;
  justify-content: center;
}

.zone-mid {
  pointer-events: none;
}

.zone-bottom {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 0 1rem;
  transform: scale(0.85);
  transform-origin: top center;
}

.preheading {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #a08060;
  margin: 0;
}

.locally {
  font-family: 'Balthazar', serif;
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  font-size: 2.5rem;
  line-height: 1;
  text-shadow: 0 0 4px rgba(255, 253, 245, 0.8);
}

.grown {
  font-family: 'Cedarville Cursive', cursive;
  font-weight: 400;
  font-size: 3rem;
  line-height: 1;
  margin-top: -0.25rem;
  color: #5a7a3a;
  text-shadow: 0 0 4px rgba(255, 253, 245, 0.8);
}

.title {
  font-family: 'Puppies Play', cursive;
  font-size: 2.8rem;
  font-weight: 400;
  line-height: 1.2;
  color: #4a3728;
  margin-bottom: 0.15rem;
  text-shadow: 0 0 4px rgba(255, 253, 245, 0.8);
}

.divider {
  font-size: 1.2rem;
  color: #c9a87c;
  margin-bottom: 0.25rem;
  text-shadow: 0 0 3px rgba(255, 253, 245, 0.8);
}

.details {
  margin-bottom: 0.5rem;
}

.detail-item {
  font-size: 0.85rem;
  line-height: 1.8;
  color: #6b5744;
  margin-bottom: 0.2rem;
  text-shadow: 0 0 3px rgba(255, 253, 245, 0.8);
}

.location-link {
  color: #a08060;
  text-decoration: none;
  border: 1.5px solid #c9a87c;
  border-radius: 20px;
  padding: 0.15rem 0.5rem;
  font-size: 0.8rem;
  transition:
    background-color 0.2s,
    color 0.2s;
}

.location-link:hover {
  background-color: #c9a87c;
  color: #fff;
}

.buttons-row {
  display: flex;
  gap: 0.75rem;
  justify-content: center;
  align-items: center;
  margin-top: 0.5rem;
}

.registry-link {
  display: inline-block;
  padding: 8px 32px;
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 0.9rem;
  letter-spacing: 0.15em;
  color: #fff;
  background-color: #c9a87c;
  border: none;
  border-radius: 20px;
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
  .hero-container {
    width: 100%;
    height: auto;
    aspect-ratio: auto;
  }

  .hero-bg {
    width: 100%;
    height: auto;
    object-fit: initial;
  }

  .title {
    font-size: 2rem;
  }

  .locally {
    font-size: 1.8rem;
  }

  .grown {
    font-size: 2.2rem;
  }
}

@media (min-aspect-ratio: 16/9) {
  .registry-link {
    padding: 16px 64px;
    font-size: 1.8rem;
  }

  .location-link {
    padding: 0.3rem 1rem;
    font-size: 1.6rem;
  }

  .detail-item {
    font-size: 1.7rem;
  }

  .title {
    font-size: 5.6rem;
  }
}
</style>
