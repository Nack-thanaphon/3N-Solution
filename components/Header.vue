<template>
  <header class="sticky top-0 z-50 bg-white/80 backdrop-blur border-b border-gray-200">
    <nav class="section-container py-4 flex items-center justify-between">
      <div class="flex items-center gap-2">
        <a href="#" class="w-10 h-10 bg-gradient-to-br from-primary to-secondary rounded-lg flex items-center justify-center">
          <span class="text-white font-bold text-lg">{{ content.site.logoText }}</span>
        </a>
        <div class="hidden sm:block">
          <h1 class="text-lg font-bold text-gray-900">{{ content.site.brandName }}</h1>
          <p class="text-xs text-gray-500">{{ content.site.brandTagline }}</p>
        </div>
      </div>

      <div class="hidden md:flex items-center gap-8">
        <a
          v-for="link in content.nav.links"
          :key="link.href"
          :href="link.href"
          class="text-gray-600 hover:text-primary transition-colors"
        >
          {{ link.label }}
        </a>
        <a :href="content.nav.cta.href" class="btn-primary text-sm">{{ content.nav.cta.label }}</a>
      </div>

      <button
        type="button"
        class="md:hidden p-2 hover:bg-gray-100 rounded-lg"
        :aria-expanded="isMenuOpen"
        aria-label="Open menu"
        @click="isMenuOpen = !isMenuOpen"
      >
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
      </button>
    </nav>

    <div v-if="isMenuOpen" class="md:hidden border-t border-gray-200 bg-white">
      <div class="section-container py-4 flex flex-col gap-2">
        <a
          v-for="link in content.nav.links"
          :key="link.href"
          :href="link.href"
          class="px-3 py-2 rounded-lg text-gray-700 hover:bg-gray-50"
          @click="isMenuOpen = false"
        >
          {{ link.label }}
        </a>
        <a
          :href="content.nav.cta.href"
          class="btn-primary w-full"
          @click="isMenuOpen = false"
        >
          {{ content.nav.cta.label }}
        </a>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import content from '~/assets/data/site.json'

const isMenuOpen = ref(false)
</script>
