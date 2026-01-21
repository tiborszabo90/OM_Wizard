<script setup>
import { ref } from 'vue'

const domain = ref('')
const isLoading = ref(false)

const handleSubmit = () => {
  if (!domain.value.trim()) return
  isLoading.value = true
  // TODO: implement submit logic
  console.log('Domain submitted:', domain.value)
  setTimeout(() => {
    isLoading.value = false
  }, 1500)
}
</script>

<template>
  <div class="min-h-screen bg-white flex items-center justify-center p-6">
    <div class="w-full max-w-md">
      <!-- Logo / Branding -->
      <div class="text-center mb-10">
        <img
          src="https://www.optimonk.com/wp-content/uploads/optimonk-logo-2024.svg"
          alt="OptiMonk"
          class="h-8 mx-auto mb-6"
        />
        <h1 class="text-3xl font-bold text-gray-900 mb-3">AI Popup Wizard</h1>
        <p class="text-gray-500">Generate on-brand popups for your website in 60 seconds.</p>
      </div>

      <form @submit.prevent="handleSubmit" class="space-y-6">
          <!-- Domain input -->
          <div>
            <label for="domain" class="block text-sm font-medium text-gray-700 mb-2">
              What's your domain?
            </label>
            <div class="relative">
              <span class="absolute left-4 top-1/2 -translate-y-1/2 text-gray-400">
                https://
              </span>
              <input
                id="domain"
                v-model="domain"
                type="text"
                placeholder="Enter website URL"
                class="w-full pl-20 pr-4 py-3 bg-white border border-gray-300 rounded-xl text-gray-900 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-orange-500 focus:border-transparent transition-all"
              />
            </div>
          </div>

          <!-- Submit button -->
          <button
            type="submit"
            class="w-full py-3 px-6 bg-[#ED5A29] text-white font-semibold rounded-xl hover:bg-[#d94f22] focus:outline-none focus:ring-2 focus:ring-[#ED5A29] focus:ring-offset-2 transition-all flex items-center justify-center gap-2 shadow-lg shadow-[#ED5A29]/25"
          >
            <svg
              v-if="isLoading"
              class="animate-spin h-5 w-5"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
            >
              <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
              <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
            </svg>
            <span>{{ isLoading ? 'Loading...' : 'Get recommendations' }}</span>
          </button>
        </form>

      <!-- Footer text -->
      <p class="text-center text-gray-400 text-sm mt-6">
        No email address needed.
      </p>
    </div>
  </div>
</template>
