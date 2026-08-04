<script setup>
import { Icon } from '@iconify/vue';
import { useSwipe } from '@vueuse/core';
import { computed, ref, useTemplateRef } from 'vue';

import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';

const isShow = ref(false)

const swRef = useTemplateRef('swRef')
const currentSwIndex = ref(0)
const activePage = ref('Home')

const menus = ref([
  { id: '1', text: 'Home' },
  { id: '2', text: 'Skill' },
  { id: '3', text: 'Project' },
  { id: '4', text: 'Education' },
  { id: '5', text: 'Achievement' },
])

const sw = ref({
  str: [
    { id: 1, value: "Adaptif" },
    { id: 2, value: "Suka bekerja di lapangan" },
    { id: 3, value: "Mampu Berbahasa Inggris" },
  ],
  weak: [
    { id: 1, value: "Terlalu memikirkan banyak hal" },
    { id: 2, value: "Mudah tertidur saat tidak melakukan apapun" },
    { id: 3, value: "Perlu meningkatkan kemampuan public speaking" }
  ]
})

const Keahlian = ref({
  main: [
    { img: "/skill/html.jpg", name: "HTML" },
    { img: "/skill/tailwindcss.png", name: "Tailwindcss" },
    { img: "/skill/js.png", name: "Javascript" },
    { img: "/skill/node.png", name: "NodeJs" },
    { img: "/skill/vue.svg", name: "Vue" },
    { img: "/skill/react.png", name: "React" },
    { img: "/skill/vite.svg", name: "Vite" },
    { img: "/skill/postgres.png", name: "Postgres" },
    { img: "/skill/github.png", name: "Github" }
  ],
  learning: [
    { img: "/skill/nestjs.png", name: "NestJs" },
    { img: "/skill/docker.png", name: "Docker" }
  ]
})

const information = ref([
  { icon: "bx:map", text: "Jakarta, Indonesia" },
  { icon: "ic:twotone-email", text: "nabixka@gmail.com" },
])

const project = ref([
  {
    name: "Mossify",
    link: "https://mossify.nabixka.my.id",
    description: "Website ini adalah website untuk menjual produk kokedama. Costumer bisa melihat lihat kokedama yang ada dan mengirim pesan kepada penjual. Menggunakan SPA",
    image: '/project/Mossify.png'
  },
  {
    name: "Findit",
    link: "https://findit-download-web.vercel.app",
    description: "DIbuat untuk membantu sesorang yang kehilangan barang/menemukan barang. Dilengkapi dengan fitur Map untuk melihat lokasi barang yang hilang.",
    image: '/project/Findit.png'
  }
])

const education = ref([
  {
    year: '2024 - 2027',
    title: 'SMK Negeri 10 Jakarta',
    major: 'Rekayasa Perangkat Lunak dan Game',
    detail: 'Membuat website, aplikasi, dan game dengan menggunakan bahasa pemrograman dan framework yang relevan.'
  }
])

const achievement = ref([
  {
    title: 'LKS Cloud Computing 2026',
    type: 'Wilayah',
    detail: 'Mendapatkan Juara 2 LKS Cloud Computing tingkat wilayah DKI Jakarta Timur 2 pada tahun 2026.'
  },
])

const totalSwSlides = 2
const navigateSw = (direction) => {
  if (direction === 'left' && currentSwIndex.value < totalSwSlides - 1) {
    currentSwIndex.value++
  } else if (direction === 'right' && currentSwIndex.value > 0) {
    currentSwIndex.value--
  }
}

useSwipe(swRef, {
  onSwipeEnd(_, direction) {
    navigateSw(direction)
  }
})

const umur = computed(() => {
  const birthDate = new Date('2008-12-27')
  const today = new Date()
  let age = today.getFullYear() - birthDate.getFullYear()
  const monthDiff = today.getMonth() - birthDate.getMonth()

  if (monthDiff < 0 || (monthDiff === 0 && today.getDate() < birthDate.getDate())) {
    age--
  }
  return age
})
</script>

<template class="font-[Open_Sans]">

  <!-- Navbar Bar -->
  <nav class="fixed top-3 left-3 right-3 z-30">
    <div class="flex justify-center">
      <div class="flex gap-5 justify-between rounded-2xl bg-zinc-700 px-4 py-2">
        <button v-for="i in menus" :key="i.text" @click="activePage = i.text"
          :class="activePage === i.text ? 'text-white font-semibold' : 'text-gray-400'"
          class="hover:cursor-pointer transition-colors text-sm">
          {{ i.text }}
        </button>
      </div>
    </div>
  </nav>

  <!-- Hero / Home Section -->
  <section v-if="activePage == 'Home'" ref="aboutRef"
    class="text-white bg-linear-to-r/hsl from-zinc-950 to-zinc-900 min-h-screen flex flex-col justify-center gap-10 pt-5">
    <div class="flex justify-between gap-5 pb-5 lg:flex-row flex-col-reverse px-5 lg:px-20">
      <div
        class="rounded-lg lg:from-zinc-900/0 lg:to-zinc-800/0 bg-linear-to-r from-zinc-900 to-zinc-800 p-5 flex flex-col justify-between w-full lg:w-1/2">
        <h5 class="flex items-center gap-1 text-lg font-semibold text-orange-400">
          Halo, <span class="text-orange-300">Saya</span>
        </h5>
        <h1 class="text-2xl lg:text-4xl font-bold">Muhammad Fadhil Abiprayana</h1>
        <h3 class="font-semibold text-xl lg:text-2xl text-orange-400">
          Web Developer <span class="text-white">| Front-end</span>
        </h3>
        <p class="text-sm py-2 lg:text-base text-zinc-300">
          Saya adalah seorang pelajar dan programmer yang memiliki semangat tinggi dalam dunia teknologi, khususnya
          dalam pengembangan web.
        </p>

        <div class="grid grid-cols-2 gap-3 py-2">
          <span v-for="i in information" :key="i.text"
            class="text-sm p-2 border border-zinc-700 rounded-lg flex items-center gap-2">
            <Icon :icon="i.icon" color="#f7bd62" width="22" />
            {{ i.text }}
          </span>

          <span class="text-sm p-2 border border-zinc-700 rounded-lg flex items-center gap-2">
            <Icon icon="formkit:date" color="#f7bd62" width="22" />
            {{ umur }} Tahun
          </span>
        </div>

        <div class="pt-2 flex gap-3 text-zinc-300">
          <Icon width="32" icon="mdi:github" class="hover:text-white cursor-pointer" />
          <Icon width="32" icon="ic:round-facebook" class="hover:text-white cursor-pointer" />
        </div>
      </div>

      <img src="/goku.png" class="h-80 lg:h-90 w-full lg:w-1/3 object-cover rounded-lg shadow-lg shadow-black/50">
    </div>
  </section>

  <!-- Keahlian Section -->
  <section v-if="activePage == 'Skill'" id="skill"
    class="bg-linear-to-r/hsl from-zinc-950 to-zinc-900 min-h-screen px-5 lg:px-20 flex flex-col justify-center gap-10 py-10">
    <div class="flex flex-col items-center lg:gap-0 gap-10">
      <span class="flex font-bold items-center justify-center gap-1 text-2xl text-orange-400 mb-6">
        <Icon icon="mdi:code" color="#f7bd62" width="25" />Keahlian Saya
      </span>

      <!-- Layout Desktop -->
      <div class="hidden lg:grid grid-cols-2 items-start gap-8">
        <div class="flex flex-col items-center">
          <h3 class="text-xl font-semibold text-orange-300 mb-3">Main</h3>
          <div class="grid grid-cols-5 gap-4">
            <div v-for="m in Keahlian.main" :key="m.name"
              class="hover:scale-105 transition flex flex-col items-center justify-between bg-zinc-800 border border-zinc-700 p-3 rounded-lg w-24 h-28 shadow-md">
              <div class="flex flex-1 items-center justify-center">
                <img class="h-10 w-10 object-contain" :src="m.img" :alt="m.name">
              </div>
              <p class="mt-2 text-center text-xs font-medium text-zinc-200">{{ m.name }}</p>
            </div>
          </div>
        </div>

        <div class="flex flex-col items-center">
          <h3 class="text-xl font-semibold text-orange-300 mb-3">Learning</h3>
          <div class="flex gap-4">
            <div v-for="l in Keahlian.learning" :key="l.name"
              class="flex flex-col items-center justify-between bg-zinc-800 border border-zinc-700 p-3 rounded-lg w-24 h-28 shadow-md">
              <div class="flex flex-1 items-center justify-center">
                <img class="h-10 w-10 object-contain" :src="l.img" :alt="l.name">
              </div>
              <p class="mt-2 text-center text-xs font-medium text-zinc-200">{{ l.name }}</p>
            </div>
          </div>
        </div>
      </div>

      <!-- bg-linear-to-r/hsl from-zinc-950/90 to-zinc-900/90 -->

      <!-- Layout Mobile (Menggunakan Swiper Vue) -->
      <div class="flex flex-col lg:hidden w-full gap-3">
        <h3 class="font-bold text-center text-lg text-orange-300">Main Skill</h3>
        <Swiper :slides-per-view="3.2" :space-between="10" class="w-full">
          <SwiperSlide v-for="item in Keahlian.main" :key="item.name">
            <div
              class="flex flex-col items-center justify-center bg-zinc-800 border border-zinc-700 p-3 rounded-xl h-28 shadow">
              <img :src="item.img" :alt="item.name" class="h-10 w-10 object-contain">
              <p class="mt-2 text-xs font-medium text-center text-zinc-200">{{ item.name }}</p>
            </div>
          </SwiperSlide>
        </Swiper>
      </div>

      <div class="flex flex-col lg:hidden w-full items-center gap-3">
        <h3 class="font-bold text-center text-lg text-orange-300">Learning</h3>
        <Swiper :slides-per-view="2" :space-between="10" class="w-full">
          <SwiperSlide v-for="item in Keahlian.learning" :key="item.name">
            <div
              class="flex flex-col items-center justify-center bg-zinc-800 border border-zinc-700 p-3 rounded-xl h-28 shadow">
              <img :src="item.img" :alt="item.name" class="h-10 w-10 object-contain">
              <p class="mt-2 text-xs font-medium text-center text-zinc-200">{{ item.name }}</p>
            </div>
          </SwiperSlide>
        </Swiper>
      </div>
    </div>

    <!-- Kelebihan & Kekurangan -->
    <!-- Desktop Grid -->
    <div class="hidden lg:grid grid-cols-2 gap-5">
      <div
        class="p-6 rounded-2xl bg-gradient-to-b from-amber-500/10 to-amber-500/5 border border-amber-500/20 space-y-3">
        <div class="flex items-center gap-3 text-amber-400 font-bold text-lg">
          <Icon icon="mdi:like-outline" class="text-2xl" />
          <span>Kelebihan</span>
        </div>
        <ul class="space-y-2">
          <li v-for="s in sw.str" :key="s.id" class="flex items-start gap-3 text-sm text-zinc-300">
            <Icon icon="ei:check" class="text-amber-400 text-xl shrink-0 mt-0.5" />
            <span>{{ s.value }}</span>
          </li>
        </ul>
      </div>

      <div class="p-6 rounded-2xl bg-zinc-950/60 border border-zinc-800 space-y-3">
        <div class="flex items-center gap-3 text-zinc-400 font-bold text-lg">
          <Icon icon="mdi:dislike-outline" class="text-2xl text-amber-500/70" />
          <span>Kekurangan</span>
        </div>
        <ul class="space-y-2">
          <li v-for="w in sw.weak" :key="w.id" class="flex items-start gap-3 text-sm text-zinc-400">
            <Icon icon="meteor-icons:circle-xmark" class="text-zinc-500 text-base shrink-0 mt-0.5" />
            <span>{{ w.value }}</span>
          </li>
        </ul>
      </div>
    </div>

    <!-- Mobile Swiper (Kelebihan / Kekurangan) -->
    <div class="flex lg:hidden mb-5 flex-col text-white">
      <div class="overflow-hidden" ref="swRef">
        <div class="flex w-full transition-transform duration-300 ease-out"
          :style="{ transform: `translateX(-${currentSwIndex * 100}%)` }">
          <!-- Kelebihan Slide -->
          <div
            class="w-full shrink-0 p-5 rounded-2xl bg-gradient-to-b from-amber-500/10 to-amber-500/5 border border-amber-500/20 space-y-3">
            <div class="flex items-center gap-2 text-amber-400 font-bold text-lg">
              <Icon icon="mdi:like-outline" class="text-xl" />
              <span>Kelebihan</span>
            </div>
            <ul class="space-y-2">
              <li v-for="s in sw.str" :key="s.id" class="flex items-start gap-2 text-sm text-zinc-300">
                <Icon icon="ei:check" class="text-amber-400 text-lg shrink-0" />
                <span>{{ s.value }}</span>
              </li>
            </ul>
          </div>

          <!-- Kekurangan Slide -->
          <div class="w-full shrink-0 p-5 rounded-2xl bg-zinc-950/60 border border-zinc-800 space-y-3">
            <div class="flex items-center gap-2 text-zinc-400 font-bold text-lg">
              <Icon icon="mdi:dislike-outline" class="text-xl text-amber-500/70" />
              <span>Kekurangan</span>
            </div>
            <ul class="space-y-2">
              <li v-for="w in sw.weak" :key="w.id" class="flex items-start gap-2 text-sm text-zinc-400">
                <Icon icon="meteor-icons:circle-xmark" class="text-zinc-500 text-base shrink-0" />
                <span>{{ w.value }}</span>
              </li>
            </ul>
          </div>
        </div>

        <!-- Pagination Dots Mobile -->
        <div class="flex justify-center gap-2 mt-4">
          <button v-for="(_, idx) in totalSwSlides" :key="idx" @click="currentSwIndex = idx"
            class="h-2 rounded-full transition-all duration-300"
            :class="currentSwIndex === idx ? 'w-6 bg-orange-400' : 'w-2 bg-zinc-700'"></button>
        </div>
      </div>
    </div>
  </section>

  <!-- Project -->
  <section v-if="activePage == 'Project'" class="text-gray-400 bg-linear-to-r/hsl from-zinc-950 to-zinc-900 min-h-screen">
    <div class="flex flex-col items-center gap-5 pt-[15%] lg:pt-[5%] pb-10">
      <div class="mb-10 text-center">
        <h2 class="mt-4 text-3xl font-bold text-white">Project</h2>
        <p class="mt-2 text-sm text-slate-300">Beberapa Project yang telah saya kerjakan.</p>
      </div>
      <a :href="i.link" v-for="(i, index) in project" :key="index" :class="index % 2 === 0 ? 'lg:flex-row' : 'lg:flex-row-reverse'" class="flex-col-reverse flex lg:w-3/5 gap-5 p-3 rounded h-full lg:border-l lg:border-r border-gray-500">
        <div class="flex flex-col lg:justify-between gap-1 h-50">
          <div class="flex flex-col gap-2">
            <h3 class="text-2xl text-white font-semibold">{{ i.name }}</h3>
            <h5>{{ i.description }}</h5>
          </div>
          <a class="text-lg text-yellow-700">View Project</a>
        </div>
        <img class="w-100 h-50 rounded" :src="i.image">
      </a>
    </div>
  </section>

  <!-- Education -->
  <section v-if="activePage == 'Education'"
    class="text-gray-400 bg-linear-to-r/hsl from-zinc-950 to-zinc-900 min-h-screen px-5 lg:px-20 py-16">
    <div class="mx-auto max-w-5xl">
      <div class="mb-10 text-center">
        <h2 class="mt-4 text-3xl font-bold text-white">Jejak Pendidikan & Proses Belajar</h2>
        <p class="mt-2 text-sm text-slate-300">Kisah perjalanan pendidikan dan semangat belajar yang terus berkembang.</p>
      </div>

      <div class="space-y-5">
        <div v-for="item in education" :key="item.title"
          class="relative overflow-hidden rounded-2xl bg-gradient-to-b from-amber-500/40 to-amber-500/5 border border-amber-500/20 p-5 shadow-lg shadow-cyan-950/30 backdrop-blur-sm">
          <div class="absolute inset-y-0 left-0 w-1 bg-gradient-to-b from-amber-300 to-amber-500"></div>
          <div class="ml-4 flex flex-col gap-2 lg:flex-row lg:items-center lg:justify-between">
            <div>
              <p class="text-xs font-semibold uppercase text-amber-300">{{ item.year }}</p>
              <h3 class="text-xl font-semibold text-white">{{ item.title }}</h3>
              <p class="text-sm text-amber-300">{{ item.major }}</p>
            </div>
            <p class="max-w-2xl text-sm leading-6 text-slate-300">{{ item.detail }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Achievement -->
  <section v-if="activePage == 'Achievement'"
    class="text-gray-400 bg-linear-to-r/hsl from-zinc-950 to-zinc-900 min-h-screen px-5 lg:px-20 py-16">
    <div class="mx-auto max-w-5xl">
      <div class="mb-10 text-center">
        <h2 class="mt-4 text-3xl font-bold text-white">Prestasi & Target Perkembangan</h2>
        <p class="mt-2 text-sm text-slate-300">Bagian ini menampilkan pencapaian yang sudah didapat serta arah pengembangan diri.</p>
      </div>

      <div class="grid gap-5 lg:grid-cols-3">
        <div v-for="item in achievement" :key="item.title"
          class="rounded-2xl bg-gradient-to-b from-amber-500/40 to-amber-500/5 border border-amber-500/20 p-5 shadow-lg  backdrop-blur-sm">
          <div class="mb-4 flex items-center justify-between">
            <span class="rounded-full bg-amber-300/15 px-3 py-1 text-xs font-semibold text-amber-200">{{ item.type }}</span>
            <Icon icon="mdi:star-circle-outline" class="text-amber-300" width="24" />
          </div>
          <h3 class="text-lg font-semibold text-white">{{ item.title }}</h3>
          <p class="mt-3 text-sm leading-6 text-slate-300">{{ item.detail }}</p>
        </div>
      </div>
    </div>
  </section>
   
</template>