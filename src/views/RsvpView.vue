<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

declare const hcaptcha: { render: (id: string, opts: Record<string, string>) => void }

const router = useRouter()

onMounted(() => {
  const id = 'web3forms-captcha-script'
  if (document.getElementById(id)) {
    if (typeof hcaptcha !== 'undefined') {
      hcaptcha.render('h-captcha', { sitekey: '50b2fe65-b00b-4b9e-ad62-3ba471098be2' })
    }
    return
  }
  const script = document.createElement('script')
  script.id = id
  script.src = 'https://web3forms.com/client/script.js'
  script.async = true
  script.defer = true
  document.body.appendChild(script)
})

const form = ref({
  name: '',
  email: '',
  guests: '1',
  message: '',
})

const isSubmitting = ref(false)
const submitError = ref('')

async function handleSubmit() {
  isSubmitting.value = true
  submitError.value = ''

  const hCaptchaEl = document.querySelector<HTMLTextAreaElement>(
    'textarea[name=h-captcha-response]',
  )
  const hCaptchaResponse = hCaptchaEl?.value

  if (!hCaptchaResponse) {
    submitError.value = 'Please complete the captcha.'
    isSubmitting.value = false
    return
  }

  try {
    const response = await fetch('https://api.web3forms.com/submit', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        access_key: 'dfbd4cda-f610-4956-a46f-678f349a14b0',
        subject: `Baby Shower RSVP from ${form.value.name}`,
        from_name: form.value.name,
        'h-captcha-response': hCaptchaResponse,
        ...form.value,
      }),
    })

    const data = await response.json()

    if (data.success) {
      router.push('/')
    } else {
      submitError.value = 'Something went wrong. Please try again.'
    }
  } catch {
    submitError.value = 'Could not submit. Please check your connection and try again.'
  } finally {
    isSubmitting.value = false
  }
}

function goBack() {
  router.push('/')
}
</script>

<template>
  <main class="rsvp">
    <div class="form-container">
      <button class="back-link" @click="goBack">&larr; Back</button>
      <h1 class="form-title">RSVP</h1>
      <p class="form-subtitle">We'd love to celebrate with you!</p>

      <form class="form" @submit.prevent="handleSubmit">
        <div class="form-group">
          <label for="name">Name</label>
          <input id="name" v-model="form.name" type="text" required placeholder="Your full name" />
        </div>

        <div class="form-group">
          <label for="email">Email</label>
          <input
            id="email"
            v-model="form.email"
            type="email"
            required
            placeholder="your@email.com"
          />
        </div>

        <div class="form-group">
          <label for="guests">Number of Guests</label>
          <select id="guests" v-model="form.guests">
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="5">5+</option>
          </select>
        </div>

        <div class="form-group">
          <label for="message">Message for Hannah &amp; Cap (optional)</label>
          <textarea
            id="message"
            v-model="form.message"
            rows="4"
            placeholder="Any dietary restrictions, notes, or well-wishes..."
          />
        </div>

        <div id="h-captcha" class="h-captcha" data-captcha="true"></div>

        <p v-if="submitError" class="error">{{ submitError }}</p>

        <button type="submit" class="submit-button" :disabled="isSubmitting">
          {{ isSubmitting ? 'Sending...' : 'Send RSVP' }}
        </button>
      </form>
    </div>
  </main>
</template>

<style scoped>
.rsvp {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  padding: 2rem;
}

.form-container {
  width: 100%;
  max-width: 500px;
  background: #fff;
  border-radius: 8px;
  padding: 2.5rem;
  box-shadow: 0 2px 20px rgba(74, 55, 40, 0.08);
}

.back-link {
  background: none;
  border: none;
  color: #a08060;
  cursor: pointer;
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 0.95rem;
  padding: 0;
  margin-bottom: 1.5rem;
  display: inline-block;
}

.back-link:hover {
  color: #4a3728;
}

.form-title {
  font-size: 2rem;
  font-weight: 400;
  color: #4a3728;
  margin-bottom: 0.5rem;
  text-align: center;
  letter-spacing: 0.1em;
}

.form-subtitle {
  text-align: center;
  color: #a08060;
  font-size: 1rem;
  margin-bottom: 2rem;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}

.form-group label {
  font-size: 0.9rem;
  color: #6b5744;
  letter-spacing: 0.05em;
}

.form-group input,
.form-group select,
.form-group textarea {
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 1rem;
  padding: 0.75rem;
  border: 1px solid #e0d5c8;
  background: #fdf6f0;
  color: #4a3728;
  transition: border-color 0.2s ease;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #c9a87c;
}

.form-group textarea {
  resize: vertical;
}

.h-captcha {
  display: flex;
  justify-content: center;
}

.error {
  color: #c0392b;
  font-size: 0.9rem;
  text-align: center;
}

.submit-button {
  padding: 14px 32px;
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 1.1rem;
  letter-spacing: 0.12em;
  color: #fff;
  background-color: #c9a87c;
  border: none;
  cursor: pointer;
  transition:
    background-color 0.3s ease,
    transform 0.2s ease;
  margin-top: 0.5rem;
}

.submit-button:hover:not(:disabled) {
  background-color: #b8956a;
  transform: translateY(-2px);
}

.submit-button:active:not(:disabled) {
  transform: translateY(0);
}

.submit-button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}
</style>

<style>
.h-captcha iframe {
  border-radius: 25px !important;
  border: 1px solid #e0d5c8 !important;
}
</style>
