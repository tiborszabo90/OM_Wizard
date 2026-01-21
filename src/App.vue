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
  <div class="min-h-screen bg-gradient-to-br from-slate-900 via-slate-800 to-slate-900 flex items-center justify-center p-6">
    <div class="w-full max-w-md">
      <!-- Logo / Branding -->
      <div class="text-center mb-10">
        <h1 class="text-3xl font-bold text-white mb-2">OM Wizard</h1>
        <p class="text-slate-400">Add meg a domain neved a kezdéshez</p>
      </div>

      <!-- Card -->
      <div class="bg-white/5 backdrop-blur-lg rounded-2xl border border-white/10 p-8">
        <form @submit.prevent="handleSubmit" class="space-y-6">
          <!-- Domain input -->
          <div>
            <label for="domain" class="block text-sm font-medium text-slate-300 mb-2">
              Domain
            </label>
            <div class="relative">
              <span class="absolute left-4 top-1/2 -translate-y-1/2 text-slate-500">
                https://
              </span>
              <input
                id="domain"
                v-model="domain"
                type="text"
                placeholder="example.com"
                class="w-full pl-20 pr-4 py-3 bg-slate-800/50 border border-slate-700 rounded-xl text-white placeholder-slate-500 focus:outline-none focus:ring-2 focus:ring-orange-500 focus:border-transparent transition-all"
              />
            </div>
          </div>

          <!-- Submit button -->
          <button
            type="submit"
            :disabled="!domain.trim() || isLoading"
            class="w-full py-3 px-6 bg-gradient-to-r from-orange-500 to-pink-500 text-white font-semibold rounded-xl hover:from-orange-600 hover:to-pink-600 focus:outline-none focus:ring-2 focus:ring-orange-500 focus:ring-offset-2 focus:ring-offset-slate-900 disabled:opacity-50 disabled:cursor-not-allowed transition-all flex items-center justify-center gap-2"
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
            <span>{{ isLoading ? 'Feldolgozás...' : 'Tovább' }}</span>
          </button>
        </form>
      </div>

      <!-- Footer text -->
      <p class="text-center text-slate-500 text-sm mt-6">
        A domain megadásával elfogadod a felhasználási feltételeket
      </p>
    </div>
  </div>
</template>
