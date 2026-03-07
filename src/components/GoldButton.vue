<script setup lang="ts">
import { useRouter } from 'vue-router'

const props = defineProps<{
  to?: string
  href?: string
  submit?: boolean
  disabled?: boolean
}>()

const router = useRouter()

function handleClick() {
  if (props.to) {
    router.push(props.to)
  }
}
</script>

<template>
  <button
    v-if="to"
    type="button"
    class="gold-button"
    @click="handleClick"
  >
    <slot />
  </button>
  <button
    v-else-if="submit"
    type="submit"
    class="gold-button"
    :disabled="disabled"
  >
    <slot />
  </button>
  <a
    v-else-if="href"
    class="gold-button"
    :href="href"
    target="_blank"
    rel="noopener noreferrer"
  >
    <slot />
  </a>
</template>
