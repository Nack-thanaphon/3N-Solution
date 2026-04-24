<template>
  <section id="who-we-are" class="py-20 md:py-28 bg-white">
    <div class="section-container">
      <div class="max-w-3xl mx-auto mb-16">
        <h2 class="heading-md mb-4">{{ content.whoWeAre.title }}</h2>
        <p class="text-lg text-muted leading-relaxed">{{ content.whoWeAre.lead }}</p>
      </div>

      <div class="grid md:grid-cols-3 gap-8">
        <div v-for="card in content.whoWeAre.cards" :key="card.title" class="card card-hover p-8">
          <div
            class="w-14 h-14 rounded-lg flex items-center justify-center mb-4 text-white"
            :class="card.theme === 'primary'
              ? 'bg-primary'
              : card.theme === 'secondary'
                ? 'bg-secondary'
                : 'bg-violet-600'"
          >
            <svg v-if="card.icon === 'network'" class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
            </svg>
            <svg v-else-if="card.icon === 'software'" class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4m0 0l-4 4m4-4H3" />
            </svg>
            <svg v-else class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
            </svg>
          </div>
          <h3 class="text-xl font-bold text-gray-900 mb-3">{{ card.title }}</h3>
          <p class="text-gray-700 leading-relaxed">{{ card.body }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import content from '~/assets/data/site.json'
</script>
