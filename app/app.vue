<script setup>
import BaseNav from './components/BaseNav.vue'

useHead({
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  link: [
    { rel: 'icon', href: '/favicon.ico' }
  ],
  htmlAttrs: {
    lang: 'en'
  }
})

const title = 'Staco - Finance'
const description = ''

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description
  // ogImage: '/app/assets/svg/logo.svg',
  // twitterImage: '/app/assets/svg/logo.svg',
  // twitterCard: 'summary_large_image'
})
</script>

<template>
  <UApp>
    <UMain>
      <BaseNav />
      <NuxtPage />
    </UMain>

    <TheFooter />
  </UApp>
</template>
