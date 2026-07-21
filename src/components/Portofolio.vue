<script setup>
import { Icon } from '@iconify/vue';
import { useWindowScroll } from '@vueuse/core';
import { computed, ref } from 'vue';

const { y } = useWindowScroll()
const about = ref()
const activeNavbar = ref('1')
const isShow = ref(false)

const menus = ref([
  { id:"1", 'text': 'About Me'},
  { id:"2", 'text': 'Keahlian Saya'},
  { id:"3",'text': 'Project'},
  { id:"4", 'text': 'Pendidikan'},
  { id:"5", 'text': 'Prestasi'},
])

const sw = ref({
  str: [
    { value: "Disiplin dan bertanggung jawab" },
    { value: "Mampu Berbahasa Inggris" },
    { value: "Adaptif" },
    { value: "Suka bekerja di lapangan"}
  ],
  weak: [
    { value: "Terlalu memikirkan banyak hal" },
    { value: "Mudah tertidur saat tidak melakukan apapun" },
    { value: "Perlu meningkatkan kemampuan public speaking"}
  ]
})

const Keahlian = ref({
  main: [
    { img: "/html.jpg", name: "HTML" },
    { img: "/tailwindcss.png", name: "Tailwindcss" },
    { img: "/js.png", name: "Javascript" },
    { img: "/node.png", name: "NodeJs" },
    { img: "/vue.svg", name: "Vue" },
    { img: "/react.png", name: "React" },
    { img: "/vite.svg", name: "Vite" },
    { img: "/postgres.png", name: "Postgres" },
    { img: "/github.png", name: "Github" }
  ],
  learning: [
    { img: "/nestjs.png", name: "NestJs" },
    { img: "/docker.png", name: "Docker" }
  ]
})

const information = ref([
  { icon: "bx:map", text: "Jakarta, Indonesia" },
  { icon: "ic:twotone-email", text: "nabixka@gmail.com" },
])

const bar = (active) => {
  return activeNavbar.value == active ? "text-white lg:text-orange-400 transition bg-orange-400 lg:bg-zinc-950/0" : "text-white"
} 

const umur = () => {
  const birthDate = new Date('2008-12-27')
  const date = new Date()

  let umur = date.getFullYear() - birthDate.getFullYear()
  const bulan = date.getMonth() - birthDate.getMonth()

  if (bulan < 0 || bulan === 0 && date.getDate() < birthDate.getDate()) {
    umur--
  }

  return umur
}

</script>

<template>
  <Transition
    enter-active-class="transition-opacity duration-300 ease-out"
    enter-from-class="opacity-0"
    enter-to-class="opacity-100"
    leave-active-class="transition-opacity duration-300 ease-in"
    leave-from-class="opacity-100"
    leave-to-class="opacity-0" >
    <div 
      v-if="isShow" 
      @click="isShow = false" 
      class="fixed inset-0 bg-black/50 z-40"
    ></div>
  </Transition>

  <Transition
    enter-active-class="transition-transform duration-300 ease-out"
    enter-from-class="translate-x-full"
    enter-to-class="translate-x-0"
    leave-active-class="transition-transform duration-300 ease-in"
    leave-from-class="translate-x-0"
    leave-to-class="translate-x-full" >
    <div v-if="isShow" class="fixed top-0 right-0 bottom-0 h-screen w-4/5 sm:w-2/5 bg-zinc-800 z-50 text-white shadow-xl flex flex-col" >
      <div class="flex justify-between items-center p-5 border-b border-zinc-700">
        <h3 class="font-bold text-2xl">Nabixka</h3>
        <button @click="isShow = false" class="p-1 text-zinc-400 hover:text-white">
          <Icon icon="mdi:close" width="28" />
        </button>
      </div>

      <div class="flex flex-col items-start pt-3">
        <button 
          v-for="menu in menus" 
          :key="menu.id" 
          @click="activeNavbar = menu.id; isShow = false" 
          :class="bar(menu.id)" 
          class="font-semibold border-b border-zinc-700/50 hover:cursor-pointer py-3.5 w-full text-start pl-6 transition-colors" >
          {{ menu.text }}
        </button>
      </div>
    </div>
  </Transition>

  <!-- Home -->
  <section
    ref="aboutRef"
    class="text-white bg-linear-to-r/hsl from-zinc-950 to-zinc-900 min-h-screen flex flex-col gap-15">
    <!-- Bar -->
    <div class="flex p-3 pl-0 items-center justify-between text-white border-b ml-2 mr-2 lg:ml-20 lg:mr-20">
      <div class="flex items-end">
        <img class="w-10" src="/public/N_logo.png">
        <h3 class="text-2xl font-semibold">abixka</h3>
      </div>

      <!-- Dekstop -->
      <div class="gap-10 hidden lg:flex">
        <button v-for="menu in menus" @click="activeNavbar = menu.id" :class="bar(menu.id)" class="hover:cursor-pointer">{{ menu.text }}</button>
      </div>

      <!-- Android -->
      <Button @click="isShow = true" class="flex lg:hidden">
        <Icon icon="pajamas:hamburger" width="33"></Icon>
      </Button>

      <div class="hidden lg:flex"></div>
    </div>

    <!-- About Me -->
    <div class="flex justify-between gap-3 lg:flex-row flex-col-reverse pl-3 pr-3 lg:pl-20 lg:pr-20">
      <div class="flex flex-col justify-between w-full lg:w-1/2">
        <h5 class="flex items-center gap-1 text-lg font-semibold text-orange-400">Halo, 
          <span class="text-orange-300 pr-1">Saya</span>
        </h5>
        <h1 class="text-2xl lg:text-4xl font-bold">Muhammad Fadhil Abiprayana</h1>
        <h3 class="font-semibold text-xl lg:text-2xl text-orange-400">Web Developer <span class="text-white">| Cloud
            Engineer</span></h3>
        <h6 class="text-sm pt-1 pb-1 lg:pt-0 lg:pb-0 lg:text-md ">Saya adalah seorang pelajar dan programmer yang memiliki semangat tinggi dalam dunia teknologi, khususnya
          dalam pengembangan web. Saya suka membangun aplikasi yang bermanfaat.</h6>

        <!-- Information -->
        <div class="grid grid-cols-2 gap-3">
          <span v-for="i in information" class="text-sm md:text-md p-2 border border-gray-200 rounded rounded-lg flex items-center gap-2">
            <Icon :icon="i.icon" color="#f7bd62" width="24"></Icon>
            {{ i.text }}
          </span>
          
          <span class="text-sm md:text-md p-2 border border-gray-200 rounded rounded-lg flex items-center gap-2">
            <Icon icon="formkit:date" color="#f7bd62" width="24"></Icon>
            {{ umur() }} Tahun
          </span>
        </div>
        <div class="pt-2 lg:pt-0">
          <Icon width="35" icon="mdi:github" />
        </div>
      </div>
      <img src="/goku.png" class="w-1/3 h-90 w-full lg:w-1/3  lg:w rounded-lg shadow-lg shadow-gray-900">
    </div>
  </section>

  <!-- Keahlian -->
  <section id="skill" class="min-h-screen bg-linear-to-r/hsl from-zinc-950/90 to-zinc-900/90 pl-20 flex flex-col gap-15 pr-20">
    <div>
      <span class="flex font-bold items-center justify-center pt-5 gap-3 text-2xl text-orange-400">
        <Icon icon="mdi:code" color="#f7bd62" width="25"></Icon>Keahlian Saya
      </span>

      <div class="grid grid-cols-2 items-start gap-5">
        <!-- Main -->
        <div class="flex flex-col items-center justify-center">
          <h3 class="text-xl font-semibold text-orange-300">Main</h3>
          <div class="grid grid-cols-5 flex gap-5 pt-2">
            <div v-for="m in Keahlian.main" :key="m.name"
              class="hover:scale-105 hover:bg-gray-100 transition flex flex-col items-center justify-between bg-white shadow-lg p-3 rounded-lg w-25 h-30">
              <div class="flex flex-1 items-center justify-center">
                <img class="h-12 w-12 object-contain" :src="m.img" :alt="m.name">
              </div>
              <p class="mt-2 text-center text-sm font-medium text-gray-700">{{ m.name }}</p>
            </div>
          </div>
        </div>

        <!-- Learning -->
        <div class="flex flex-col items-center justify-center">
          <h3 class="text-xl font-semibold text-orange-300">Learning</h3>
          <div class="flex gap-5 pt-2">
            <div v-for="l in Keahlian.learning" :key="l.name"
              class="flex flex-col items-center justify-between bg-white shadow-lg p-3 rounded-lg w-25 h-30">
              <div class="flex flex-1 items-center justify-center">
                <img class="h-12 w-12 object-contain" :src="l.img" :alt="l.name">
              </div>
              <p class="mt-2 text-center text-sm font-medium text-gray-700">{{ l.name }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Kekurangan/Kelebihan -->
    <div class="grid grid-cols-2 gap-5">
        <!-- Kelebihan -->
        <div class="p-6 rounded-2xl bg-gradient-to-b from-amber-500/10 to-amber-500/5 border border-amber-500/20 space-y-4">
          <div class="flex items-center gap-3 text-amber-400 font-bold text-lg">
            <Icon icon="mdi:like-outline" class="text-2xl" /> 
            <span>Kelebihan</span>
          </div>
          <ul class="space-y-2">
            <li v-for="s in sw.str" :key="s.value" class="flex items-start gap-3 text-sm text-zinc-300">
              <Icon icon="ei:check" class="text-amber-400 text-xl shrink-0 mt-0.5" />
              <span>{{ s.value }}</span>
            </li>
          </ul>
        </div>

        <!-- Kekurangan -->
        <div class="p-6 rounded-2xl bg-zinc-950/60 border border-zinc-800 space-y-4">
          <div class="flex items-center gap-3 text-zinc-400 font-bold text-lg">
            <Icon icon="mdi:dislike-outline" class="text-2xl text-amber-500/70" /> 
            <span>Kekurangan</span>
          </div>
          <ul class="space-y-2">
            <li v-for="w in sw.weak" :key="w.value" class="flex items-start gap-3 text-sm text-zinc-400">
              <Icon icon="meteor-icons:circle-xmark" class="text-zinc-500 text-base shrink-0 mt-0.5" />
              <span>{{ w.value }}</span>
            </li>
          </ul>
        </div>
      </div>
  </section>

  <section class="bg-linear-to-r/hsl from-zinc-900 via-gray-800/80 to-gray-700/70 min-h-screen text-white">

  </section>

</template>