<template>
  <div class="relative pb-25 bg-[#ECF1F1]">
    <footer class="bg-[#ECF1F1] w-full pt-[7vw] relative z-10 px-5 sm:px-10 xl:px-0">
      <div class="max-w-292.5 mx-auto bg-[#1F2334] rounded-2xl mb-50 ">
        <div class="flex flex-wrap gap-8 p-[5vw]">
          <div class="w-75">
            <AppLogo class="" />

            <p class="text-[#B4B5BA] mt-10 font-semibold leading-6">
              Staco is the dedicated platform for performance management that helps to grow your startup quickly
            </p>

            <div class="flex gap-3 mt-10">
              <div
                v-for="social in socials"
                :key="social"
                class="w-10 h-10 flex justify-center items-center rounded-full cursor-pointer border border-[#434654]"
              >
                <Icon
                  :name="social"
                  class="text-white text-lg"
                />
              </div>
            </div>
          </div>

          <div class="w-full grid grid-cols-2 md:grid-cols-4 items-start justify-around">
            <div
              v-for="item in footerNavs"
              :key="item.title"
              class=""
            >
              <h3 class="uppercase font-extrabold text-white mb-4">
                {{ item.title }}
              </h3>
              <p
                v-for="child in item.children"
                :key="child.title"
                class="text-[#B4B5BA] text-[15px] font-semibold py-2.5"
              >
                {{ child.title }}
              </p>
            </div>
          </div>
        </div>

        <div class="flex flex-col-reverse md:flex-row justify-center md:justify-between items-center gap-4 py-6 px-[5vw] text-white border-t border-[#333747]">
          <p class="text-[#B4B5BA] text-[15px] font-semibold">
            2023 Staco. All rights reserved.
          </p>
          <div class="flex gap-4 text-[#B4B5BA] text-[15px] font-semibold">
            <nuxt-link
              to="#"
              class="hover:text-white cursor-pointer"
            >
              Terms and conditions
            </nuxt-link>
            <nuxt-link
              to="#"
              class="hover:text-white cursor-pointer"
            >
              Cookies
            </nuxt-link>
            <nuxt-link
              to="#"
              class="hover:text-white cursor-pointer"
            >
              Privacy policy
            </nuxt-link>
          </div>
        </div>
      </div>
    </footer>
    <div class="relative h-fit z-0 hidden">
      <div class="max-w-292.5 mx-auto fixed bottom-0 left-1/2 -translate-x-1/2 w-full bg-[#ECF1F1] z-0">
        <p class="font-extrabold">
          Disclaimer:
        </p>
        <p class="text-sm font-normal leading-7 mt-4">
          There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration
          in some form, by injected humour, or randomised words which don't look even slightly believable.
          If you are going to use a passage of Lorem Ipsum, you need to be sure there isn't anything
          embarrassing hidden in the middle of text. All the Lorem Ipsum generators on the Internet
          tend to repeat predefined chunks as necessary.
        </p>

        <p class="text-sm font-normal leading-7 mt-4 mb-17">
          Making this the first true generator on the Internet. It uses a dictionary of over 200 Latin words,
          combined handful of model sentence structures, to generate which looks reasonable.
          The generated Lorem Ipsum is therefore always
        </p>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const socials = ref(['line-md:facebook', 'ri:twitter-x-line', 'flowbite:linkedin-solid', 'ri:instagram-line', 'ri:youtube-fill'])

const footerNavs = [
  {
    title: 'Products 🔥',
    children: [
      { title: 'HR Management' },
      { title: 'Invoice System' },
      { title: 'Email Marketing' },
      { title: 'Web Services' },
      { title: 'Digital Marketing' }
    ]
  },
  {
    title: 'Why choose 🌟',
    children: [
      { title: 'Customers' },
      { title: 'Why Staco?' },
      { title: 'Book a demo' }
    ]
  },
  {
    title: 'Resources ❇️',
    children: [
      { title: 'Latest blog' },
      { title: 'Supports' },
      { title: 'Knowledgebase' },
      { title: 'FAQs' }
    ]
  },
  {
    title: 'Company 💎',
    children: [
      { title: 'About' },
      { title: 'What we do' },
      { title: 'Contact us' },
      { title: 'Careers' }
    ]
  }
]
</script>
