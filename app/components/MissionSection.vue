<template>
  <div class="px-5 sm:px-10 xl:px-0">
    <div
      class="max-w-292.5 mx-auto bg-[#004D42] rounded-4xl relative grid grid-cols-1
      md:grid-cols-2 justify-center lg:justify-left "
    >
      <div class="p-[5vw]">
        <h2
          class="text-4xl lg:text-5xl leading-14 lg:leading-16 text-center lg:text-left
        font-extrabold text-white max-w-lg"
        >
          We are building financial foundations
        </h2>
        <UButton
          class="group rounded-full bg-mint hover:bg-[#44C486] text-white font-semibold mx-auto lg:mx-0
        cursor-pointer mt-10 px-10 py-5 transition-all duration-300 ease-in-out flex items-center gap-3"
        >
          <p class="font-extrabold text-black group-hover:text-white transition-all duration-300 ease-in-out">
            Let's Talk
          </p>
          <Icon
            name="lucide:arrow-right"
            class="text-xl font-bold text-black group-hover:text-white group-hover:-rotate-30
          transition-all duration-300 ease-in-out"
          />
        </UButton>
      </div>
      <div
        ref="containerRef"
        class="image-container"
      >
        <FinancialFoundationsIcon
          ref="imageRef"
          class="parallax-img"
        />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import gsap from 'gsap'
import FinancialFoundationsIcon from './icons/FinancialFoundationsIcon.vue'

import { onMounted, ref } from 'vue'

const containerRef = ref<HTMLElement>()
const imageRef = ref<HTMLElement>()

onMounted(() => {
  if (!containerRef.value || !imageRef.value) return

  // Set initial position
  gsap.set(imageRef.value, { x: -200 }) // move left initially

  const observer = new IntersectionObserver(([entry]) => {
    console.log({ entry, imageRef: imageRef.value })
    if (entry && entry.isIntersecting && imageRef.value) {
      gsap.to(imageRef.value, {
        x: 0,
        duration: 2,
        ease: 'power4.out'
      })

      observer.disconnect() // stop observing
    }
  }, { threshold: 0.3 }) // trigger when 30% visible

  observer.observe(containerRef.value)
})
</script>

<style scoped>
.image-container {
  position: relative;
  height: 300px;
  overflow: hidden;
}

.parallax-img {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
}
</style>
