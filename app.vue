<template>
  <div class="min-h-screen bg-white">
    <Header />
    <main>
      <ImageSlider v-if="siteContent.slider.enabled" :slides="siteContent.slider.slides" />
      <HeroSection />
      <PainPoints :content="siteContent.painPoints" />
      <Presentation />
      <WhoWeAre />
      <WhatWeDo />
      <OurApproach />
      <CaseExamples />
      <Testimonials :content="siteContent.testimonials" />
      <TeamSection />
      <Articles :content="siteContent.articles" />
      <ContactSection />
    </main>
    <Footer />
  </div>
</template>

<script setup lang="ts">
import siteContent from '~/assets/data/site.json'
import Header from '~/components/Header.vue'
import ImageSlider from '~/components/ImageSlider.vue'
import HeroSection from '~/components/HeroSection.vue'
import PainPoints from '~/components/PainPoints.vue'
import WhoWeAre from '~/components/WhoWeAre.vue'
import WhatWeDo from '~/components/WhatWeDo.vue'
import OurApproach from '~/components/OurApproach.vue'
import CaseExamples from '~/components/CaseExamples.vue'
import Testimonials from '~/components/Testimonials.vue'
import TeamSection from '~/components/TeamSection.vue'
import Articles from '~/components/Articles.vue'
import ContactSection from '~/components/ContactSection.vue'
import Footer from '~/components/Footer.vue'
import Presentation from '~/components/Presentation.vue'

useHead({
  title: siteContent.site.title,
  meta: [
    {
      name: 'description',
      content: siteContent.site.description,
    },
  ],
})
</script>
