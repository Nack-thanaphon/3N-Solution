<template>
  <section id="pain-points" class="py-20 md:py-28 bg-gray-50">
    <div class="section-container">
      <div class="max-w-3xl mx-auto mb-16 text-center">
        <h2 class="heading-md mb-4">{{ content.title }}</h2>
        <p class="text-lg text-gray-600 leading-relaxed">
          {{ content.lead }}
        </p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div 
          v-for="(point, index) in content.points" 
          :key="index"
          class="p-6 bg-white rounded-lg border border-gray-200 hover:border-red-300 hover:shadow-lg transition-all"
        >
          <div class="flex items-start gap-4 mb-4">
            <div class="flex-shrink-0 w-12 h-12 bg-red-100 rounded-lg flex items-center justify-center">
              <svg class="w-6 h-6 text-red-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path v-if="point.icon === 'downtime'" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                <path v-else-if="point.icon === 'data'" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4m0 5c0 2.21-3.582 4-8 4s-8-1.79-8-4" />
                <path v-else-if="point.icon === 'outsourcing'" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" />
                <path v-else-if="point.icon === 'security'" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z" />
                <path v-else-if="point.icon === 'expensive'" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                <path v-else-if="point.icon === 'slow'" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z" />
              </svg>
            </div>
            <div>
              <h3 class="text-lg font-bold text-gray-900">{{ point.title }}</h3>
            </div>
          </div>
          <p class="text-gray-600">{{ point.body }}</p>
        </div>
      </div>

      <div class="text-center mt-12">
        <a href="tel:+66XXXXXXXXXX" class="btn-primary inline-flex items-center gap-2">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502.1.006l-2.048 1.029a2 2 0 00-2.063.063l-3.034 2.024a1 1 0 00-.97-.004l-2.49-1.245a1 1 0 00-.502.756l-1.498 4.493a1 1 0 00.948.684H21a2 2 0 012 2v2.75a.75.75 0 01-1.5 0V19H4.75v2.25a.75.75 0 01-1.5 0V5z" />
          </svg>
          โทรปรึกษาฟรี
        </a>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
defineProps<{
  content: {
    title: string
    lead: string
    points: Array<{
      icon: string
      title: string
      body: string
    }>
  }
}>()
</script>
