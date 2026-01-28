<template>
  <div>
    <div class="hidden md:block absolute w-full !z-[99]">
      <div class="max-w-fit mx-auto flex rounded-full border-2 p-1 border-[#3F3F3F] mt-4">
        <div class="mx-auto relative">
          <div
            class="flex justify-center items-center h-full gap-2 before:absolute before:inset-0 before:rounded-full
            before:bg-linear-to-t before:from-white/10 before:to-transparent
            after:absolute after:inset-0 after:rounded-full
            after:bg-lnear-to-b after:from-black/20 after:to-transparent rounded-full"
          >
            <AppLogo class="mr-4" />
            <div
              v-for="item in navItems"
              :key="item.name"
              class="cursor-pointer z-9"
              @click="activeNav = item.name"
            >
              <p
                class="px-5 flex items-center rounded-full h-12 text-sm text-white font-semibold transition-all duration-800 ease-in-out"
                :class="{ 'bg-[#C2C2C2] !text-[#171717]': item.name === activeNav }"
              >
                {{ item.name }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="md:hidden h-20 px-8 flex items-center">
      <img :src="LogoMobile">
      <Icon
        name="ri:menu-3-fill"
        class=" text-[#444444] text-2xl ml-auto cursor-pointer"
        @click="modalOpen = true"
      />
    </div>

    <div
      v-if="modalOpen"
      class="block md:hidden fixed bg-[rgba(0,0,0,0.1)] top-0 bottom-0 left-0 right-0 z-99"
    >
      <div class="w-[90%] bg-white h-screen">
        <div class="h-20 px-4 flex items-center justify-between">
          <img :src="LogoMobile">
          <Icon
            name="lucide:x"
            class=" text-[#444444] text-2xl cursor-pointer"
            @click="modalOpen = false"
          />
        </div>

        <div class="px-5">
          <div
            v-for="item in navItems"
            :key="item.name"
            class="cursor-pointer z-9"
            @click="activeNav = item.name"
          >
            <p
              class="flex items-center text-sm font-bold transition-all duration-800 ease-in-out py-4 border-b border-[#b3b1b1]"
            >
              {{ item.name }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import LogoMobile from '../assets/images/logo-mobile.png'

const route = useRoute()
const currentPath = computed(() => route.path)
const activeNav = ref('Home')

console.log({ currentPath: currentPath.value })

const modalOpen = ref(false)

const navItems = ref([
  { name: 'Home', link: '/' },
  { name: 'Pages', link: '/pages' },
  { name: 'Services', link: '/services' },
  { name: 'Blog', link: '/blog' },
  { name: 'Contact Us', link: '/contact-us' }
])
</script>

<style scoped>

</style>
