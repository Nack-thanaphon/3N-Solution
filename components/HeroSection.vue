<template>
  <section class="relative py-20 md:py-28 bg-gradient-to-br from-gray-50 via-white to-gray-50 overflow-hidden">
    <div class="absolute inset-0 pointer-events-none">
      <div class="absolute -top-24 -left-24 w-80 h-80 bg-primary/10 rounded-full blur-3xl"></div>
      <div class="absolute -bottom-24 -right-24 w-80 h-80 bg-secondary/10 rounded-full blur-3xl"></div>
    </div>

    <div class="section-container relative">
      <div class="max-w-4xl mx-auto text-center">
        <div class="inline-flex items-center gap-2 mb-6 px-4 py-2 bg-white/80 border border-gray-200 rounded-full text-sm font-semibold text-gray-700">
          <span class="w-2 h-2 rounded-full bg-secondary"></span>
          <span>{{ content.hero.badge }}</span>
        </div>

        <h1 class="heading-lg mb-6 leading-snug">
          {{ content.hero.title }}<br />
          <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">{{ content.hero.highlight }}</span>
        </h1>

        <p class="text-lg md:text-xl text-muted mb-10 leading-relaxed">
          {{ content.hero.subtitle }}
        </p>

        <div class="flex flex-col sm:flex-row gap-3 justify-center">
          <a :href="content.hero.primaryCta.href" class="btn-primary">
            {{ content.hero.primaryCta.label }}
          </a>
          <a :href="content.hero.secondaryCta.href" class="btn-outline">
            {{ content.hero.secondaryCta.label }}
          </a>
        </div>

        <div class="mt-16 grid grid-cols-1 sm:grid-cols-3 gap-6">
          <div v-for="stat in content.hero.stats" :key="stat.label" class="card px-6 py-7">
            <div class="text-3xl font-bold text-gray-900">{{ stat.value }}</div>
            <p class="text-gray-600 text-sm mt-2">{{ stat.label }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import content from '~/assets/data/site.json'
</script>
