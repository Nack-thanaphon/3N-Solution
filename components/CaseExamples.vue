<template>
  <section id="cases" class="py-20 md:py-28 bg-gray-50">
    <div class="section-container">
      <div class="max-w-3xl mx-auto mb-16">
        <h2 class="heading-md mb-4">{{ content.cases.title }}</h2>
        <p class="section-lead">{{ content.cases.lead }}</p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="item in content.cases.items" :key="item.title" class="bg-white rounded-lg overflow-hidden shadow-sm hover:shadow-md transition-shadow">
          <div class="h-48 overflow-hidden">
            <img v-if="item.image" :src="item.image" :alt="item.title" class="w-full h-full object-cover" />
            <div
              v-else
              class="h-full flex items-center justify-center"
              :class="item.theme === 'primary'
                ? 'bg-gradient-to-br from-primary to-primary/80'
                : item.theme === 'secondary'
                  ? 'bg-gradient-to-br from-secondary to-secondary/80'
                  : 'bg-gradient-to-br from-violet-600 to-violet-500'"
            >
              <svg v-if="item.icon === 'monitoring'" class="w-24 h-24 text-white opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
              </svg>
              <svg v-else-if="item.icon === 'dashboard'" class="w-24 h-24 text-white opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
              <svg v-else-if="item.icon === 'plc'" class="w-24 h-24 text-white opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
              </svg>
              <svg v-else-if="item.icon === 'dev'" class="w-24 h-24 text-white opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4m0 0l-4 4m4-4H3" />
              </svg>
              <svg v-else-if="item.icon === 'infra'" class="w-24 h-24 text-white opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
              </svg>
              <svg v-else class="w-24 h-24 text-white opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" />
              </svg>
            </div>
          </div>

          <div class="p-6">
            <h3 class="text-xl font-bold text-gray-900 mb-2">{{ item.title }}</h3>
            <p class="text-gray-600 mb-4 card-body">{{ item.body }}</p>
            <div class="space-y-2">
              <div v-for="bullet in item.bullets" :key="bullet" class="flex items-center gap-2 text-sm text-gray-700">
                <span
                  class="w-2 h-2 rounded-full"
                  :class="item.theme === 'primary'
                    ? 'bg-primary'
                    : item.theme === 'secondary'
                      ? 'bg-secondary'
                      : 'bg-violet-600'"
                ></span>
                <span>{{ bullet }}</span>
              </div>
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
