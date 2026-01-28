<template>
  <div class="w-full bg-[#ECF1F1] pt-[7vw] px-5 sm:px-10 xl:px-0">
    <div class="max-w-292.5 mx-auto bg-white rounded-2xl">
      <div class="grid grid-cols-1 md:grid-cols-2 justify-center">
        <div
          class="flex justify-center items-end relative pt-10"
        >
          <img
            :src="SlideImage"
            class="absolute top-10 left-0 h-50"
          >

          <div class="image-wrapper">
            <img :src="currentTestimony.image">
          </div>
        </div>
        <div class="">
          <UCarousel
            ref="carousel"
            v-slot="{ item }"
            v-model="activeCarouselIndex"
            class="w-full mx-auto"
            loop
            wheel-gestures
            :autoplay="{ delay: 7000 }"
            :items="testimonials"
          >
            <div class="mt-20 px-10">
              <img
                :src="QuoteImage"
                class="w-17"
              >
              <p class="font-semibold text-[17px] leading-8 text-[#444444] mt-12">
                {{ item.content }}
              </p>
              <p class="font-bold mt-10">
                {{ item.name }}
              </p>
              <p class="font-semibold mt-1">
                {{ item.role }}
              </p>
            </div>
          </UCarousel>
        </div>
      </div>
      <div class="progress-track mt-8">
        <div class="progress-bar" />
      </div>
      <div class="py-6 px-5 flex justify-around items-center">
        <img
          v-for="logo in logos"
          :key="logo"
          :src="logo"
          class="max-w-[18%]"
        >
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import PeterLeo from '../assets/images/peter-leo.png'
import DennisLail from '../assets/images/dennis-lail.png'
import RoeSmith from '../assets/images/roe-smith.png'
import ArthoueDe from '../assets/images/arthoue-de.png'
import QuoteImage from '../assets/images/quote.png'
import SlideImage from '../assets/images/slide.png'
import JQueryLogo from '../assets/images/jQuery.png'
import GithubLogo from '../assets/images/github.png'
import PortisLogo from '../assets/images/portis.png'
import EnvatoLogo from '../assets/images/envato.png'
import DaomakLogo from '../assets/images/daomak.png'

const carousel = ref()
const activeCarouselIndex = ref(0)
const testimonials = ref([
  {
    content: `Very denounce with righteous indignation and dislike men who are so beguiled 
      and demoralized by the charms of pleasure of the moment, combined with a handfulso 
      blinded by desire encounter 🥰 🤜 🤛`,
    name: 'Peter Leo',
    image: PeterLeo,
    role: 'CTO - Criston'
  },
  {
    content: `Making this the first true 😍 generator on the Internet. It uses a dictionary of over words, 
      combined with a handful of model sentence structures, to generate 👏👏`,
    name: 'Dennis Lail',
    image: DennisLail,
    role: 'Marketer'
  },
  {
    content: `I must explain to you how all this mistaken. Tdea of denouncing pleasure and praising 
      pain was born and I will give you a complete account. 😍`,
    name: 'Roe Smith',
    image: RoeSmith,
    role: 'Director, Growth Marketing'
  },
  {
    content: `We use as filler text for layouts, non-readability is of great importance but because those 
      who do not know how to pleasure rationally encounter consequences that are pleasure rationally encounter ❤️ ❤️`,
    name: 'Arthue De',
    image: ArthoueDe,
    role: 'CEO - Dorid Co'
  }
])

const logos = ref([
  JQueryLogo,
  GithubLogo,
  PortisLogo,
  EnvatoLogo,
  DaomakLogo
])

const currentTestimony = computed(() => testimonials.value[activeCarouselIndex.value]!)
</script>

<style scoped>
.image-wrapper {
  width: 300px;
  height: 300px;
  background: #004D42;
  border-top-left-radius: 50%;
  border-top-right-radius: 50%;
  padding: 20px 20px 0 20px;
  display: flex;
  justify-content: center;
  position: relative;
  z-index: 3;
  margin-left: -20px;
}

.image-wrapper > img {
  z-index: 9;
}

.image-wrapper::before {
  position: absolute;
  content: '';
  z-index: 0;
  top: 0px;
  right: 20px;
  width: 300px;
  height: 300px;
  background: #A8E198;
  border-top-left-radius: 50%;
  border-top-right-radius: 50%;
  padding: 20px 20px 0 20px;
  display: flex;
  justify-content: center;
}

.progress-track {
  height: 3px;
  width: 100%;
  background: #e5e7eb;
  overflow: hidden;
  border-radius: 9999px;
}

.progress-bar {
  height: 100%;
  background: #44C486;
  animation: fill-reset 10s linear infinite;
}

@keyframes fill-reset {
  0% {
    width: 0%;
  }
  100% {
    width: 100%;
  }
}
</style>
