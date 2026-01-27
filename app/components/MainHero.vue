<template>
  <div class="w-full min-h-[75vh] bg-[#1F2334]">
    <div class="max-w-292.5 mx-auto ">
      <div class="text-6xl font-bold pt-[12vw] leading-20 text-white">
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
          overflow-hidden h-12.5 cursor-pointer
          transition-all duration-300 ease-in-out hover:scale-105"
        >
          <div
            class="flex flex-col items-center gap-5
            translate-y-3
            group-hover:-translate-y-7
            transition-transform duration-300 ease-in-out
            px-8 py-4"
          >
            <p class="pt-3">
              Get Started For Free
            </p>
            <p class="">
              Get Started For Free
            </p>
          </div>
        </UButton>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import gsap from 'gsap'

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
