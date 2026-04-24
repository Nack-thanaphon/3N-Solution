<template>
  <section id="approach" class="py-20 md:py-28 bg-white">
    <div class="section-container">
      <div class="max-w-3xl mx-auto mb-16">
        <h2 class="heading-md mb-4">{{ content.approach.title }}</h2>
        <p class="text-lg text-muted leading-relaxed">{{ content.approach.lead }}</p>
      </div>

      <div class="grid md:grid-cols-4 gap-6">
        <div v-for="(step, index) in content.approach.steps" :key="step.title" class="card p-6">
          <div class="flex items-center gap-4 mb-4">
            <div class="w-12 h-12 rounded-full bg-primary text-white flex items-center justify-center font-bold text-lg">
              {{ index + 1 }}
            </div>
            <h3 class="text-lg font-bold text-gray-900">{{ step.title }}</h3>
          </div>
          <p class="text-gray-600 text-sm leading-relaxed">{{ step.body }}</p>
        </div>
      </div>

      <!-- Benefits -->
      <div class="mt-20 pt-20 border-t border-gray-200">
        <h3 class="text-2xl font-bold text-gray-900 mb-8 text-center">{{ content.approach.benefitsTitle }}</h3>
        <div class="grid md:grid-cols-3 gap-8">
          <div v-for="benefit in content.approach.benefits" :key="benefit.title" class="flex gap-4">
            <div class="flex-shrink-0">
              <div class="flex items-center justify-center h-12 w-12 rounded-md bg-primary text-white">
                <svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
              </div>
            </div>
            <div>
              <h4 class="text-lg font-bold text-gray-900">{{ benefit.title }}</h4>
              <p class="text-gray-600 mt-2">{{ benefit.body }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import content from '~/assets/data/site.json'
</script>
