<template>
  <div class="w-full min-h-[75vh] bg-[#1F2334] overflow-hidden">
    <div class="max-w-292.5 mx-auto h-full relative">
      <div class="grid grid-cols-1 md:grid-cols-2 md:pt-[18vw] lg:pt-[12vw]">
        <div class="">
          <div class="md:text-4xl lg:text-6xl font-bold md:leading-15 lg:leading-20 text-white">
            <h1>
              Financial Security
            </h1>
            <h1 class="flex">
              Made <div class="ml-2 w-fit container">
                <span id="text-element text-mint">Easier</span>
                <div id="underline" />
              </div>
            </h1>
          </div>

          <div class="mt-8 max-w-2xl text-lg text-white">
            <p>
              Staco is the dedicated platform for human management that helps to grow your startup business quickly
            </p>
          </div>

          <div>
            <UButton
              class="group mt-8 rounded-full bg-[#44C486] hover:bg-mint text-white font-semibold
              overflow-hidden h-15 cursor-pointer
              transition-all duration-300 ease-in-out hover:scale-105"
            >
              <div
                class="flex flex-col items-center gap-5
                  translate-y-3 group-hover:-translate-y-7
                  transition-transform duration-300 ease-in-out
                  px-8 py-4"
              >
                <p class="pt-3.5">
                  Get Started For Free
                </p>
                <p class="">
                  Get Started For Free
                </p>
              </div>
            </UButton>
          </div>
        </div>

        <div class="relative">
          <video
            ref="heroVideo"
            class="max-w-115 max-h-85 w-full h-full rounded-3xl object-cover"
            autoplay
            loop
            muted
          >
            <source
              src="../assets/video/hero.mp4"
              type="video/mp4"
            >
          </video>
          <HeroCurl class="absolute -top-30 -left-20 text-[250px] text-transparent" />
          <HeroCurlBottom class="absolute -bottom-65 -left-20 text-[250px] text-transparent" />
          <button
            class="flex justify-center items-center bg-white h-12 w-12 rounded-full absolute bottom-4 right-4"
            @click="toggleVideo"
          >
            <Icon
              name="simple:play"
              class="text-mint"
              width="100"
              height="100"
            />
            <Icon
              name="lucide:pause"
              class="text-mint"
              width="100"
              height="100"
            />
          </button>
        </div>
      </div>

      <!-- bg elements -->
      <div class="absolute top-0 right-0 bottom-0 left-0 w-full h-full">
        <div class="w-full h-full relative">
          <HeroTopLeft class="absolute left-[6vw] top-[12vw] text-[#63a582] text-5xl" />
          <HeroTopRight class="absolute right-[5vw] top-[12vw] text-[#63a582] text-5xl" />
          <HeroMiddle class="absolute left-[25vw] top-[25vw] text-[#63a582] text-5xl" />
          <HeroMiddleBottom class="absolute left-[25vw] bottom-[8vw] text-[#63a582] text-5xl" />
          <HeroBottomLeft class="absolute left-[5vw] bottom-[8vw] text-[#63a582] text-5xl" />
          <HeroBottomRight class="absolute right-[5vw] bottom-[8vw] text-[#63a582] text-5xl" />
        </div>
      </div>
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

const toggleVideo = () => {
  if (heroVideo.value) {
    if (heroVideo.value.paused) {
      heroVideo.value.play()
    } else {
      heroVideo.value.pause()
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
