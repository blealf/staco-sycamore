<template>
  <div class="max-w-292.5 mx-auto mb-[7vw] px-5 sm:px-10 xl:px-0">
    <p class="font-extrabold uppercase text-[#44C486] tracking-[5px] text-center">
      Benefits
    </p>
    <h2 class="font-extrabold text-5xl text-center max-w-125 leading-16 mt-3 mx-auto">
      {{ `Most used features \n You must need` }}
    </h2>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-10">
      <div class="bg-[#ECEFF1] p-10 rounded-4xl">
        <UCarousel
          ref="carousel"
          v-slot="{ item }"
          v-model="activeCarouselIndex"
          class="w-full mx-auto"
          loop
          wheel-gestures
          :autoplay="{ delay: 7000 }"
          :items="benefits"
        >
          <img :src="item.image">
        </UCarousel>
      </div>
      <div class="h-full max-h-full overflow-hidden">
        <UAccordion
          v-model="accordionModel"
          :items="computedBenefits"
          :ui="{
            header: 'py-4 px-6 !border-none border-b border-[#999999]',
            trigger: '!font-extrabold text-lg cursor-pointer',
            trailingIcon: `text-[#999999] text-lg`,
            content: 'px-7 pb-4',
            body: 'text-[16px] font-semibold leading-7 text-[#444444]'
          }"
          type="single"
          collapsible
        >
          <template #trailing="{ open }">
            <UIcon
              :name="open ? 'i-lucide-minus' : 'i-lucide-plus'"
              class="ml-auto text-[#999999] text-2xl transition-transform duration-200"
              :class="{ '!text-[#44C486]': open }"
            />
          </template>
        </UAccordion>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import FinancialAdvisorImage from '../assets/images/financial-advisor-benefit.png'
import BusinessGrowthImage from '../assets/images/business-growth-benefit.png'
import MarketingPlanImage from '../assets/images/marketing-plan-benefit.png'
import EthicalFinanceImage from '../assets/images/ethical-finance-benefit.png'

const benefits = ref([
  {
    label: 'Financial advisor program',
    content: `We use as filler text for layouts, non-readability is of great importance but 
      because those who do not know how to pursue pleasure rationally encounter consequences 
      that are extremely painful. Nor again is there anyone`,
    image: FinancialAdvisorImage,
    trailingIcon: 'i-lucide-plus'
  },
  {
    label: 'Business growth',
    content: `We use as filler text for layouts, non-readability is of great importance but 
      because those who do not know how to pursue pleasure rationally encounter consequences 
      that are extremely painful. Nor again is there anyone`,
    image: BusinessGrowthImage,
    trailingIcon: 'i-lucide-plus'
  },
  {
    label: 'Marketing plan',
    content: `We use as filler text for layouts, non-readability is of great importance but 
      because those who do not know how to pursue pleasure rationally encounter consequences 
      that are extremely painful. Nor again is there anyone`,
    image: MarketingPlanImage,
    trailingIcon: 'i-lucide-plus'
  },
  {
    label: 'Ethical finance guide',
    content: `We use as filler text for layouts, non-readability is of great importance but 
      because those who do not know how to pursue pleasure rationally encounter consequences 
      that are extremely painful. Nor again is there anyone`,
    image: EthicalFinanceImage,
    trailingIcon: 'i-lucide-plus'
  }
])

const activeIndex = ref(0)
const activeCarouselIndex = ref(0)
const carousel = ref()

const accordionModel = computed({
  get: () => String(activeIndex.value),
  set: (val: string | string[]) => {
    activeIndex.value = Number(val)
  }
})

const computedBenefits = computed(() =>
  benefits.value.map((item, index) => ({
    ...item,
    value: String(index),
    active: index === activeIndex.value,
    trailingIcon:
      index === activeIndex.value
        ? 'i-lucide-minus'
        : 'i-lucide-plus'
  }))
)

watch(activeIndex, (index) => {
  console.log({ index })
  carousel.value?.emblaApi?.scrollTo(index)
})

watch(activeCarouselIndex, (index) => {
  accordionModel.value = String(index)
})
</script>

<style scoped>

</style>
