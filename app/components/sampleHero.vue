<template>
  <section class="w-full min-h-[75vh] bg-[#1F2334] overflow-hidden">
    <UContainer class="relative">
      <div class="grid grid-cols-1 md:grid-cols-2 md:pt-[18vw] lg:pt-[12vw] gap-12">
        <!-- TEXT -->
        <div>
          <h1 class="text-white font-bold md:text-4xl lg:text-6xl leading-tight">
            Financial Security
          </h1>

          <h1 class="text-white font-bold md:text-4xl lg:text-6xl flex">
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

          <p class="mt-8 max-w-2xl text-lg text-white">
            Staco is the dedicated platform for human management that helps
            grow your startup business quickly.
          </p>

          <!-- CTA -->
          <UButton
            size="xl"
            color="primary"
            variant="solid"
            class="mt-8 rounded-full font-semibold overflow-hidden h-15
                   transition-all hover:scale-105"
          >
            <span
              class="flex flex-col items-center gap-5 translate-y-3
                         group-hover:-translate-y-7 transition-transform"
            >
              <span>Get Started For Free</span>
              <span>Get Started For Free</span>
            </span>
          </UButton>
        </div>

        <!-- VIDEO -->
        <div class="relative">
          <video
            ref="heroVideo"
            autoplay
            loop
            muted
            class="w-full max-w-[460px] max-h-[340px] rounded-3xl object-cover"
          >
            <source
              src="../assets/video/hero.mp4"
              type="video/mp4"
            >
          </video>

          <!-- Play / Pause -->
          <UButton
            square
            size="lg"
            variant="solid"
            class="absolute bottom-4 right-4 rounded-full"
            @click="toggleVideo"
          >
            <NuxtIcon
              :name="isPlaying ? 'lucide:pause' : 'lucide:play'"
              size="20"
              class="text-mint"
            />
          </UButton>

          <!-- Decorative curls -->
          <NuxtIcon
            name="hero-curl"
            class="absolute -top-30 -left-20 text-[250px] text-transparent"
          />
          <NuxtIcon
            name="hero-curl-bottom"
            class="absolute -bottom-65 -left-20 text-[250px] text-transparent"
          />
        </div>
      </div>

      <!-- BACKGROUND ICONS -->
      <div class="absolute inset-0 pointer-events-none">
        <NuxtIcon
          name="hero-top-left"
          class="absolute left-[6vw] top-[12vw] text-[#63a582] text-5xl"
        />
        <NuxtIcon
          name="hero-top-right"
          class="absolute right-[5vw] top-[12vw] text-[#63a582] text-5xl"
        />
        <NuxtIcon
          name="hero-middle"
          class="absolute left-[25vw] top-[25vw] text-[#63a582] text-5xl"
        />
        <NuxtIcon
          name="hero-middle-bottom"
          class="absolute left-[25vw] bottom-[8vw] text-[#63a582] text-5xl"
        />
        <NuxtIcon
          name="hero-bottom-left"
          class="absolute left-[5vw] bottom-[8vw] text-[#63a582] text-5xl"
        />
        <NuxtIcon
          name="hero-bottom-right"
          class="absolute right-[5vw] bottom-[8vw] text-[#63a582] text-5xl"
        />
      </div>
    </UContainer>
  </section>
</template>

<script setup lang="ts">
import gsap from 'gsap'
// import HeroTopLeft from '../assets/icons/hero-top-left.svg'
// import HeroTopRight from '../assets/icons/hero-top-right.svg'
// import HeroMiddle from '../assets/icons/hero-middle.svg'
// import HeroMiddleBottom from '../assets/icons/hero-middle-bottom.svg'
// import HeroBottomLeft from '../assets/icons/hero-bottom-left.svg'
// import HeroBottomRight from '../assets/icons/hero-bottom-right.svg'
// import HeroCurl from '../assets/icons/hero-curl.svg'
// import HeroCurlBottom from '../assets/icons/hero-curl-bottom.svg'

const heroVideo = ref<HTMLVideoElement | null>(null)
const isPlaying = ref(true)

const toggleVideo = () => {
  console.log({ hero: heroVideo.value })
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
  const textEl = document.querySelector<HTMLElement>('#text-element')
  const line = document.querySelector<HTMLElement>('#underline')

  if (!textEl || !line) return

  let index = 0

  // Initial text
  textEl.textContent = words[index] ?? ''

  gsap.set(line, {
    scaleX: 0,
    transformOrigin: 'left center'
  })

  gsap.timeline({
    repeat: -1,
    onRepeat: () => {
      index = (index + 1) % words.length
      textEl.textContent = words[index] ?? ''
    }
  })
    .to(line, {
      scaleX: 1,
      duration: 0.8,
      ease: 'power2.inOut'
    })
    .to(line, {
      opacity: 0,
      duration: 0.2,
      delay: 0.5
    })
    .set(line, {
      scaleX: 0,
      opacity: 1
    })
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
