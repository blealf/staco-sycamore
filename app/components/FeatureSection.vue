<template>
  <div
    class="max-w-292.5 mx-auto grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3
    justify-center items-start gap-8 my-[7vw] px-5 sm:px-10 xl:px-0"
  >
    <div
      v-for="item in moreItems"
      :key="item.title"
      class="px-6 py-10 bg-[#ECEFF1] rounded-3xl group"
    >
      <div class="mb-5">
        <component
          :is="item.icon"
          :class="[`text-[${item.color}]`]"
          class="w-12.5 h-12.5 text-5xl [&_svg]:fill-current [&_svg]:stroke-current"
        />
      </div>
      <p class="mt-10 text-lg font-bold">
        {{ item.title }}
      </p>
      <p class="mt-8 text-[15px] font-semibold leading-7">
        {{ item.description }}
      </p>
      <div class="flex justify-between items-center mt-10 w-full cursor-pointer">
        <p
          className="text-[15px] font-extrabold text-[#444444] group-hover:text-[#44C486]
            transition-all duration-500 ease-in-out"
        >
          Learn more
        </p>

        <div
          class="w-10 h-10 rounded-full flex justify-center items-center
          bg-[#D5D7D9] group-hover:bg-[#44C486] transition-all duration-500 ease-in-out"
        >
          <Icon
            name="lucide:arrow-right"
            class="text-xl font-bold group-hover:text-white group-hover:-rotate-30
              transition-all duration-500 ease-in-out"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import UsedAdvancedIcon from './icons/UsedAdvancedIcon.vue'
import CleanDesignIcon from './icons/CleanDesignIcon.vue'
import BestCustomerIcon from './icons/BestCustomerIcon.vue'

const moreItems = ref([
  {
    title: 'Used advanced technologies',
    description: `I must explain to you how all this mistaken. 
      Idea of main denouncing pleasure and praising pain was born`,
    icon: UsedAdvancedIcon,
    color: '#99B0AD'
  },
  {
    title: 'Clean design & Typography',
    description: `I must explain to you how all this mistaken. 
      Idea of main denouncing pleasure and praising pain was born`,
    icon: CleanDesignIcon,
    color: '#B0DEC7'
  },
  {
    title: 'Best customer support',
    description: `I must explain to you how all this mistaken. 
      Idea of main denouncing pleasure and praising pain was born`,
    icon: BestCustomerIcon,
    color: '#AAA8BB'
  }
])
</script>

<style scoped>

</style>
