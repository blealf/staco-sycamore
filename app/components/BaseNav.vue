<template>
  <div class="absolute w-full">
    <div class="max-w-292.5 mx-auto flex rounded-full border-2 p-1 border-[#3F3F3F] mt-4">
      <div>
        <AppLogo />
      </div>
      <div class="mx-auto relative">
        <div
          class="flex justify-center items-center before:absolute pt-0.5 before:inset-0 before:rounded-full
            before:bg-linear-to-t before:from-white/10 before:to-transparent
            after:absolute after:inset-0 after:rounded-full
            after:bg-lnear-to-b after:from-black/20 after:to-transparent rounded-full"
        >
          <div
            v-for="item in navItems"
            :key="item.name"
          >
            <NuxtLink
              :to="item.link"
            ><p
              class="px-5 py-3 rounded-full text-sm"
              :class="{ 'bg-[#C2C2C2] text-[#171717]': item.name === activeNav }"
            >{{ item.name }}</p>
            </NuxtLink>
          </div>
        </div>
      </div>
      <div class="flex items-center gap-4 mr-3">
        <div class="flex items-center gap-2">
          <nuxt-icon
            name="lucide:globe"
            class="text-white"
            width="32"
            height="32"
            style="stroke-width: 1.75"
          />
          <p class="text-sm">
            EN
          </p>
        </div>
        <p class="text-sm">
          Sign in
        </p>
        <UButton
          label="Start free"
          class="rounded-full bg-mint text-black font-semibold"
        />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const route = useRoute()
const currentPath = computed(() => route.path)
const activeNav = ref('Home')

console.log({ currentPath: currentPath.value })

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
