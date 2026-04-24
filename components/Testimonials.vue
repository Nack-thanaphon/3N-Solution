<template>
  <section id="testimonials" class="py-20 md:py-28 bg-white">
    <div class="section-container">
      <div class="max-w-3xl mx-auto mb-16 text-center">
        <h2 class="heading-md mb-4">{{ content.title }}</h2>
        <p class="text-lg text-gray-600 leading-relaxed">
          {{ content.lead }}
        </p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(review, index) in content.reviews" 
          :key="index"
          class="p-6 bg-gradient-to-br from-gray-50 to-white rounded-lg border border-gray-200 hover:shadow-lg transition-all"
        >
          <div class="flex items-center gap-1 mb-4">
            <svg 
              v-for="n in review.rating" 
              :key="n" 
              class="w-5 h-5 text-yellow-400" 
              fill="currentColor" 
              viewBox="0 0 24 24"
            >
              <path d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z" />
            </svg>
          </div>

          <p class="text-gray-700 leading-relaxed mb-6">"{{ review.content }}"</p>

          <div>
            <div class="font-bold text-gray-900">{{ review.name }}</div>
            <div class="text-sm text-gray-600">{{ review.role }}</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
defineProps<{
  content: {
    title: string
    lead: string
    reviews: Array<{
      name: string
      role: string
      content: string
      rating: number
    }>
  }
}>()
</script>
