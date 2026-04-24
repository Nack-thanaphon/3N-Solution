<template>
  <section id="articles" class="py-20 md:py-28 bg-gray-50">
    <div class="section-container">
      <div class="max-w-3xl mx-auto mb-16 text-center">
        <h2 class="heading-md mb-4">{{ content.articles.title }}</h2>
        <p class="section-lead">
          {{ content.articles.lead }}
        </p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div 
          v-for="(article, index) in content.articles.items" 
          :key="index"
          class="bg-white rounded-lg border border-gray-200 hover:border-blue-300 hover:shadow-lg transition-all overflow-hidden"
        >
          <div class="h-40 overflow-hidden">
            <img v-if="article.image" :src="article.image" :alt="article.title" class="w-full h-full object-cover" />
            <div v-else class="h-full bg-gradient-to-br from-blue-400 to-blue-600 flex items-center justify-center">
              <svg class="w-16 h-16 text-white opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 20H5a2 2 0 01-2-2V6a2 2 0 012-2h10a2 2 0 012 2v1m2 13a2 2 0 01-2-2V7m2 13a2 2 0 002-2V9a2 2 0 00-2-2h-2m-4-3H9M7 16h6M7 8h6v4H7V8z" />
              </svg>
            </div>
          </div>
          <div class="p-6">
            <div class="flex items-center gap-2 mb-3">
              <span class="px-3 py-1 bg-blue-100 text-blue-700 rounded-full text-xs font-semibold">
                {{ article.category }}
              </span>
              <span class="text-xs text-gray-500">{{ article.readTime }}</span>
            </div>
            <h3 class="text-lg font-bold text-gray-900 mb-2 line-clamp-2">{{ article.title }}</h3>
            <p class="text-gray-600 text-sm leading-relaxed line-clamp-2">{{ article.excerpt }}</p>
          </div>
        </div>
      </div>

      <div class="text-center mt-12">
        <a href="#contact" class="btn-outline inline-flex items-center gap-2">
          Need Specific Consultation? Contact Us
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import content from '~/assets/data/site.json'
</script>

<style scoped>
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>
