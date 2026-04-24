<template>
  <section id="team" class="py-20 md:py-28 bg-white">
    <div class="section-container">
      <div class="max-w-3xl mx-auto mb-16">
        <h2 class="heading-md mb-4">{{ content.team.title }}</h2>
        <p class="section-lead">{{ content.team.lead }}</p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="member in content.team.members" :key="member.role" class="bg-white rounded-lg border border-gray-200 overflow-hidden hover:shadow-md transition-shadow">
          <div class="h-48 overflow-hidden">
            <img v-if="member.image" :src="member.image" :alt="member.role" class="w-full h-full object-cover" />
            <div
              v-else
              class="h-full flex items-center justify-center"
              :class="member.theme === 'primary'
                ? 'bg-gradient-to-br from-primary to-primary/80'
                : member.theme === 'secondary'
                  ? 'bg-gradient-to-br from-secondary to-secondary/80'
                  : 'bg-gradient-to-br from-violet-600 to-violet-500'"
            >
              <svg class="w-14 h-14 text-white" fill="currentColor" viewBox="0 0 24 24">
                <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z" />
              </svg>
            </div>
          </div>

          <div class="p-6">
            <h3 class="text-xl font-bold text-gray-900 mb-1">{{ member.role }}</h3>
            <p class="text-gray-600 mb-4">{{ member.subtitle }}</p>
            <p class="text-gray-600 text-sm leading-relaxed">{{ member.body }}</p>
          </div>
        </div>
      </div>

      <div class="max-w-4xl mx-auto mt-16 pt-16 border-t border-gray-200">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
          <div v-for="stat in content.team.stats" :key="stat.label" class="text-center">
            <div class="text-3xl md:text-4xl font-bold text-gray-900 mb-2">{{ stat.value }}</div>
            <p class="text-gray-600">{{ stat.label }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import content from '~/assets/data/site.json'
</script>
