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
          <p class="intro-line">Join us in celebrating baby Wilson, arriving June 2026.</p>
          <h1 class="pre-title">Honoring mom to be</h1>
          <h2 class="title">Hannah Wilson</h2>
          <div class="divider">&#10045;</div>
          <div class="details">
            <p class="detail-item">MAY 9TH, 2026 | 12 - 2PM</p>
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
          <p class="rsvp-by">Please RSVP by April 9th</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.home {
  position: fixed;
  inset: 0;
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

  /* Scale card with viewport: 1920×1080 = 0.75, smaller laptops scale down so nothing gets smushed */
  .hero-container {
    --scale: calc(0.75 * min(1, 100vw / 1920, 100vh / 1080));
    transform: scale(var(--scale));
  }
}

.hero-container {
  position: relative;
  height: 100%;
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
  padding: clamp(1rem, 4vh, 2.5rem) clamp(0.5rem, 3vw, 1.5rem) 0;
  transform: scale(0.85);
  transform-origin: top center;
  min-width: 0; /* allow shrinking so content can scale */
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

.intro-line {
  margin: 0.25rem 0 0.15rem;
  font-family: 'Cedarville Cursive', cursive;
  font-size: 2rem; /* 4/5 of 2.5rem */
  line-height: 1.2;
  color: #a08060;
  letter-spacing: 0.02em;
  text-shadow: 0 0 4px rgba(255, 253, 245, 0.8);
  max-width: 100%;
}

.pre-title {
  font-family: 'Balthazar', serif;
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  font-size: 1.2rem; /* 4/5 of 1.5rem */
  line-height: 1;
  text-shadow: 0 0 4px rgba(255, 253, 245, 0.8);
  padding: 12px 20px 20px;
}

.title {
  font-family: 'Cedarville Cursive', cursive;
  font-size: 2.24rem; /* 4/5 of 2.8rem */
  font-weight: 400;
  line-height: 1.2;
  color: #5a7a3a;
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
  max-width: 100%;
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
  text-align: center;
  display: inline-block;
  max-width: 100%;
  word-break: break-word;
}

.location-link:hover {
  background-color: #c9a87c;
  color: #fff;
}

.buttons-row {
  display: flex;
  flex-wrap: wrap;
  gap: clamp(0.5rem, 1.5vw, 0.75rem);
  justify-content: center;
  align-items: center;
  margin-top: 0.5rem;
}

.rsvp-by {
  margin: 0.5rem 0 0;
  font-size: 0.9rem;
  color: #8a7a6a;
  letter-spacing: 0.08em;
  font-family: 'Balthazar', serif;
  text-shadow: 0 0 2px rgba(255, 253, 245, 0.6);
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

  /* Shrink zone-bottom so buttons and RSVP text stay in the white area */
  .zone-bottom {
    transform: scale(0.72);
    transform-origin: top center;
  }

  .title {
    font-size: 1.6rem; /* 4/5 of 2rem */
  }

  .locally {
    font-size: 1.8rem;
  }

  .intro-line {
    font-size: 1.44rem; /* 4/5 of 1.8rem */
  }

  .grown {
    font-size: 2.2rem;
  }
}

/* Fluid typography and spacing for wide screens so small laptops don’t get smushed */
@media (min-aspect-ratio: 16/9) {
  .registry-link {
    padding: clamp(8px, 1.5vmin, 16px) clamp(24px, 4vmin, 64px);
    font-size: clamp(0.9rem, 2.2vmin, 1.8rem);
  }

  .location-link {
    padding: 0.2rem clamp(0.5rem, 1.5vmin, 1rem);
    font-size: clamp(0.8rem, 2vmin, 1.6rem);
  }

  .detail-item {
    font-size: clamp(0.85rem, 2vmin, 1.7rem);
  }

  .intro-line {
    font-size: clamp(1.6rem, 3.2vmin, 2.8rem); /* 4/5 of previous */
  }

  .pre-title {
    font-size: clamp(1rem, 1.8vmin, 1.28rem); /* 4/5 of previous */
  }

  .locally {
    font-size: clamp(2rem, 4vmin, 3.5rem);
  }

  .grown {
    font-size: clamp(2.2rem, 4.5vmin, 4rem);
  }

  .title {
    font-size: clamp(2rem, 4.8vmin, 4.48rem); /* 4/5 of previous */
  }

  .divider {
    font-size: clamp(1rem, 1.5vmin, 1.2rem);
  }

  .rsvp-by {
    font-size: clamp(0.85rem, 1.5vmin, 1.1rem);
  }
}
</style>
