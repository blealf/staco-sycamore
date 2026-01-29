<template>
  <div class="w-full min-h-[73vh] bg-[#1F2334] overflow-hidden px-5 sm:px-10 xl:px-0">
    <div class="max-w-292.5 mx-auto h-[73vh] relative">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 md:pt-[18vw] justify-center lg:pt-[14vw]">
        <div class="flex flex-col gap-12">
          <div class="mt-10 lg:mt-0">
            <h1 class="text-white font-extrabold text-4xl lg:text-6xl leading-20 lg:leading-30">
              Financial Security
            </h1>

            <h1 class="text-white font-bold text-4xl lg:text-6xl flex">
              Made
              <span class="ml-2 relative inline-block">
                <span
                  id="text-element"
                  class="text-mint"
                >
                  Easier
                </span>
                <span id="underline" />
              </span>
            </h1>
          </div>

          <p class="max-w-2xl text-lg text-white font-bold leading-9">
            Staco is the dedicated platform for human management that helps
            grow your startup business quickly.
          </p>

          <div class="flex gap-6 items-center">
            <UButton
              class="group rounded-full bg-[#44C486] hover:bg-mint text-white font-semibold
              overflow-hidden h-15 cursor-pointer
              transition-all duration-300 ease-in-out"
            >
              <div
                class="flex flex-col items-center gap-5
                  translate-y-3 group-hover:-translate-y-7
                  transition-transform duration-300 ease-in-out
                  px-4 lg:px-8 py-4 font-bold"
              >
                <p class="pt-3.5">
                  Get Started For Free
                </p>
                <p class="">
                  Get Started For Free
                </p>
              </div>
            </UButton>
            <div class="flex gap-3 items-center cursor-pointer group">
              <p class="text-white font-semibold group-hover:text-[#44C486] transition-all duration-500 ease-in-out">
                Let's talk
              </p>
              <div
                class="h-7 w-7 bg-[#383B4A] group-hover:bg-[#44C486] rounded-full flex
                justify-center items-center group-hover:-rotate-45 transition-all duration-500 ease-in-out"
              >
                <Icon
                  name="heroicons:chevron-right-20-solid"
                  class="text-lg text-white"
                />
              </div>
            </div>
          </div>
        </div>

        <div class="mx-auto mt-10 md:mt-0 md:ml-auto relative max-w-115 max-h-85 w-full h-full">
          <!-- Hero Video -->
          <video
            ref="heroVideo"
            class="max-w-115 max-h-85 w-full h-full rounded-3xl object-cover z-10 relative"
            autoplay
            loop
            muted
          >
            <source
              src="../assets/video/hero.mp4"
              type="video/mp4"
            >
          </video>

          <!-- Top Curl -->
          <HeroCurl
            class="hidden md:block absolute -top-30 lg:-top-50 -left-20 lg:-left-28 text-[250px] lg:text-[350px] text-transparent z-11"
          />

          <!-- Bottom Curl (behind video) -->
          <HeroCurlBottom
            class="hidden md:block absolute -bottom-65 lg:-bottom-85 -left-20 lg:-left-38
           text-[350px] lg:text-[500px] text-transparent z-0"
          />

          <!-- Play/Pause Button -->
          <button
            class="flex justify-center items-center bg-white h-12 w-12 rounded-full
           absolute bottom-4 right-4 cursor-pointer z-20"
            @click="toggleVideo"
          >
            <Icon
              v-if="isPlaying"
              name="material-symbols:pause-rounded"
              class="text-xl text-[#44C486]"
            />
            <Icon
              v-else
              name="mynaui:play-solid"
              class="text-xl text-[#44C486]"
            />
          </button>
        </div>
      </div>

      <!-- bg elements -->

      <HeroTopLeft class="absolute left-[8vw] top-[10vw] text-[#63a582] text-5xl" />
      <HeroTopRight class="absolute right-[5vw] top-[10vw] text-[#63a582] text-5xl" />
      <HeroMiddle class="absolute left-[25vw] top-[20vw] text-[#63a582] text-5xl" />
      <HeroMiddleBottom class="absolute left-[25vw] bottom-[18vw] text-[#63a582] text-5xl" />
      <HeroBottomLeft class="absolute left-[5vw] bottom-[-10] text-[#63a582] text-2xl" />
      <HeroBottomRight class="absolute right-1/2 bottom-20 text-[#63a582] text-5xl" />
    </div>
  </div>
</template>

<script setup lang="ts">
import gsap from 'gsap'
import HeroTopLeft from '../assets/icons/hero-top-left.svg'
import HeroTopRight from '../assets/icons/hero-top-right.svg'
import HeroMiddle from '../assets/icons/hero-middle.svg'
import HeroMiddleBottom from '../assets/icons/hero-middle-bottom.svg'
import HeroBottomLeft from '../assets/icons/hero-bottom-left.svg'
import HeroBottomRight from '../assets/icons/hero-bottom-right.svg'
import HeroCurl from '../assets/icons/hero-curl.svg'
import HeroCurlBottom from '../assets/icons/hero-curl-bottom.svg'

const heroVideo = ref<HTMLVideoElement | null>(null)
const isPlaying = ref(true)

const toggleVideo = () => {
  if (heroVideo.value) {
    if (heroVideo.value.paused) {
      heroVideo.value.play()
      isPlaying.value = true
    } else {
      heroVideo.value.pause()
      isPlaying.value = false
    }
  }
}

onMounted(() => {
  const words = ['Easier', 'Unbeatable', 'Accountable']
  const textEl: HTMLElement | null = document.querySelector('#text-element')
  const line = document.querySelector('#underline')

  let index = 0

  function startInfiniteLoop() {
    if (!textEl || !line) return
    const tl = gsap.timeline({
      onComplete: () => {
        // Move to next word and restart
        index = (index + 1) % words.length
        textEl.textContent = words[index] ?? ''
        startInfiniteLoop()
      }
    })

    tl.to(line, {
      scaleX: 1,
      duration: 0.8,
      ease: 'power2.inOut'
    })
      .to(line, {
        opacity: 0,
        duration: 0.2,
        delay: 0.5 // Hold for a moment so user can read
      })
      .set(line, {
        scaleX: 0,
        opacity: 1
      }) // Reset line for the next word
  }

  startInfiniteLoop()
})
</script>

<style scoped>
.container {
  display: inline-block;
  position: relative;
}

.play-btn {
  svg {
    fill: #63a582;
  }
}

#underline {
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 100%;
  height: 4px;
  background-color: #B2EDA1;
  transform: scaleX(0);
  transform-origin: left;
}
</style>
