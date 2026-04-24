<template>
  <section class="py-16 md:py-20 bg-white">
    <div class="section-container">
      <div class="max-w-3xl mx-auto text-center mb-10">
        <h2 class="heading-md mb-3">{{ content.presentation.title }}</h2>
        <p class="text-lg text-muted">{{ content.presentation.subtitle }}</p>
      </div>

      <div class="card card-hover overflow-hidden">
        <div class="relative w-full aspect-video">
          <iframe
            loading="lazy"
            class="absolute inset-0 w-full h-full border-0 p-0 m-0"
            :src="content.presentation.embedUrl"
            allowfullscreen
            allow="fullscreen"
          ></iframe>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import content from '~/assets/data/site.json'
</script>
