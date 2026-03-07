<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'
import GoldButton from '@/components/GoldButton.vue'

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
  phone: '',
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

function autoResize(event: Event) {
  const el = event.target as HTMLTextAreaElement
  el.style.height = 'auto'
  el.style.height = el.scrollHeight + 'px'
}

const formContainer = ref<HTMLElement | null>(null)

function goBack() {
  if (formContainer.value) {
    formContainer.value.style.animation = 'form-depart 0.4s cubic-bezier(0.7, 0, 0.84, 0) forwards'
    formContainer.value.addEventListener('animationend', () => router.push('/'), { once: true })
  } else {
    router.push('/')
  }
}
</script>

<template>
  <main class="rsvp">
    <div ref="formContainer" class="form-container">
      <button class="back-link" @click="goBack">&larr; Back</button>
      <h1 class="form-title">RSVP</h1>
      <p class="form-subtitle">We'd love to celebrate with you!</p>

      <form class="form" @submit.prevent="handleSubmit">
        <div class="form-group">
          <label for="name">Name</label>
          <input id="name" v-model="form.name" type="text" required placeholder="Your full name" />
        </div>

        <div class="form-group">
          <label for="phone">Phone Number</label>
          <input
            id="phone"
            v-model="form.phone"
            type="tel"
            required
            placeholder="(xxx)-xxx-xxxx"
          />
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
          <label for="message">Message for Hannah &amp; Cap (optional)</label>
          <textarea
            id="message"
            v-model="form.message"
            rows="2"
            placeholder="Any dietary restrictions, notes, or well-wishes..."
            @input="autoResize"
          />
        </div>

        <div id="h-captcha" class="h-captcha" data-captcha="true"></div>

        <p v-if="submitError" class="error">{{ submitError }}</p>

        <GoldButton submit :disabled="isSubmitting">
          {{ isSubmitting ? 'Sending...' : 'Send RSVP' }}
        </GoldButton>
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
  background: url('/images/mobile_background.png') center / cover no-repeat fixed;
}

@media (min-aspect-ratio: 16/9) {
  .rsvp {
    background: url('/images/desktop_background.png') center / cover no-repeat fixed;
  }
}

.form-container {
  width: 100%;
  max-width: 500px;
  background: #fff;
  border-radius: 50px;
  padding: 2.5rem;
  box-shadow: 0 2px 20px rgba(74, 55, 40, 0.08);
  animation: form-arrive 0.6s cubic-bezier(0.16, 1, 0.3, 1) both;
}

@keyframes form-arrive {
  from {
    opacity: 0;
    transform: translateY(40px) scale(0.96);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
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
  font-family: 'Balthazar', serif;
  font-size: 2rem;
  font-weight: 400;
  color: #4a3728;
  margin-bottom: 0.5rem;
  text-align: center;
  letter-spacing: 0.1em;
}

.form-subtitle {
  font-family: 'Cedarville Cursive', cursive;
  text-align: center;
  color: #a08060;
  font-size: 1.25rem;
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
  resize: none;
  overflow: hidden;
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

/* GoldButton submit: same gold look, bigger size */
.form :deep(.gold-button) {
  display: inline-block;
  padding: 14px 32px;
  font-family: 'Georgia', 'Times New Roman', serif;
  font-size: 1.1rem;
  letter-spacing: 0.12em;
  color: #fff;
  background-color: #c9a87c;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  transition:
    background-color 0.3s ease,
    transform 0.2s ease;
  margin-top: 0.5rem;
}

.form :deep(.gold-button:hover:not(:disabled)) {
  background-color: #b8956a;
  transform: translateY(-2px);
}

.form :deep(.gold-button:active:not(:disabled)) {
  transform: translateY(0);
}

.form :deep(.gold-button:disabled) {
  opacity: 0.6;
  cursor: not-allowed;
}
</style>

<style>
.h-captcha iframe {
  border-radius: 25px !important;
  border: 1.75px solid #e0d5c8 !important;
}

@keyframes form-depart {
  from {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
  to {
    opacity: 0;
    transform: translateY(40px) scale(0.96);
  }
}
</style>
