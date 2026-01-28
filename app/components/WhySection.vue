<template>
  <UContainer class="max-w-292.5 mx-auto my-[7vw]">
    <div class="grid grid-cols-1 md:grid-cols-2 justify-start">
      <UCarousel
        ref="whyCarousel"
        v-slot="{ item }"
        v-model="activeCarouselIndex"
        :items="opportunities"
        class="w-full mx-auto"
        loop
        wheel-gestures
        :autoplay="{ delay: 7000 }"
      >
        <div>
          <p
            class="font-extrabold uppercase tracking-[5px]"
            :style="{ color: item.titleColor }"
          >
            WHY CHOOSE US
          </p>
          <h2 class="font-extrabold text-[40px] leading-12 mt-3">
            {{ item.title }}
          </h2>

          <p class="mt-12.5 font-semibold leading-8 text-[#444444]">
            {{ item.description }}
          </p>

          <div class="grid grid-cols-2 text-[#444444] mt-8">
            <div
              v-for="benefit in item.benefits"
              :key="benefit"
              class="flex items-center gap-2 mb-6"
            >
              <Icon
                name="lucide:check"
                class="text-[#44C486]"
              />
              <p class="font-semibold">
                {{ benefit }}
              </p>
            </div>
          </div>
        </div>
      </UCarousel>
      <div class="flex gap-4 h-115 w-full">
        <div
          v-for="(item, index) in opportunities"
          :key="index"
          class="w-[20%] h-full rounded-2xl cursor-pointer transition-width duration-500 ease-in-out"
          :class="{ 'w-[50%]': index === activeIndex }"
          @click="setActiveIndex(index)"
        >
          <img
            :src="item.image"
            class="h-full object-cover rounded-2xl"
          >
        </div>
      </div>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
const activeIndex = ref(0)
const activeCarouselIndex = ref(0)
const whyCarousel = ref()

const opportunities = ref([
  {
    title: 'Discover Business Opportunities',
    titleColor: '#44C486',
    description: `We use as filler text for layouts, non-readability is of great importance but 
      because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful. 
      Nor again is there anyone`,
    benefits: [
      'Profile consultation',
      'Asset management',
      'No-risk business idea'
    ],
    image: 'https://staco-react.vercel.app/assets/feature-team1-CkrnjYrI.png'
  },
  {
    title: 'Manage team increase productivity',
    titleColor: '#0095FF',
    description: `We use as filler text for layouts, non-readability is of great importance but 
      because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful. 
      Nor again is there anyone`,
    benefits: [
      '99% Survey Report',
      'Trusted by teams',
      'Self-service'
    ],
    image: 'https://staco-react.vercel.app/assets/feature-team2-BkN4ZF3A.png'
  },
  {
    title: 'Manage team increase productivity',
    titleColor: '#0095FF',
    description: `We use as filler text for layouts, non-readability is of great importance but 
      because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful. 
      Nor again is there anyone`,
    benefits: [
      '99% Survey Report',
      'Trusted by teams',
      'Self-service'
    ],
    image: 'https://staco-react.vercel.app/assets/feature-team3-rNw9B1sS.png'
  }
])

const setActiveIndex = (val: number) => {
  activeIndex.value = val
}

watch(activeIndex, (index) => {
  whyCarousel.value?.emblaApi?.scrollTo(index)
})

watch(activeCarouselIndex, (index) => {
  activeIndex.value = index
})
</script>

<style scoped>

</style>
