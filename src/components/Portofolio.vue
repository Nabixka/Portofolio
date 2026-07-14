<script setup>
import { Icon } from '@iconify/vue';
import { ref } from 'vue';

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
    {
      img: "/src/assets/html.jpg",
      name: "HTML"
    },
    {
      img: "/src/assets/tailwindcss.png",
      name: "Tailwindcss"
    },
    {
      img: "/src/assets/js.png",
      name: "Javascript"
    },
    {
      img: "/src/assets/node.png",
      name: "NodeJs"
    },
    {
      img: "/src/assets/vue.svg",
      name: "Vue"
    },
    {
      img: "/src/assets/react.png",
      name: "React"
    },
    {
      img: "/src/assets/vite.svg",
      name: "Vite"
    },
    {
      img: "/src/assets/postgres.png",
      name: "Postgres"
    },
    {
      img: "/src/assets/github.png",
      name: "Github"
    }
  ],
  learning: [
    {
      img: "/src/assets/nestjs.png",
      name: "NestJs"
    },
    {
      img: "/src/assets/docker.png",
      name: "Docker"
    }
  ]
})

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

  <section
    class="text-white bg-linear-to-br from-gray-950/70 via-gray-800/70 to-gray-700/70 min-h-screen flex flex-col gap-15">
    <!-- Bar -->
    <div class="flex p-3 pl-20 items-center justify-between text-white">
      <h3 class="text-2xl font-semibold">M. Fadhil</h3>
      <div class="flex gap-10">
        <h5>About Me</h5>
        <h5>Keahlian Saya</h5>
        <h5>Project</h5>
        <h5>Pendidikan</h5>
        <h5>Prestasi</h5>
      </div>
      <div></div>
    </div>

    <!-- About Me -->
    <div class="flex justify-between pl-20 pr-20">
      <div class="flex flex-col justify-between w-1/2">
        <h5 class="flex items-center gap-1 text-lg font-semibold text-orange-400">Halo, <span
            class="text-orange-300 pr-1">Saya</span>
          <Icon icon="entypo:hand" color="#f7bd62"></Icon>
        </h5>
        <h1 class="text-4xl font-bold">Muhammad Fadhil Abiprayana</h1>
        <h3 class="font-semibold text-2xl text-orange-400">Web Developer <span class="text-white">| Cloud
            Engineer</span></h3>
        <h6>Saya adalah seorang pelajar dan programmer yang memiliki semangat tinggi dalam dunia teknologi, khususnya
          dalam pengembangan web. Saya suka membangun aplikasi yang bermanfaat.</h6>
        <div class="flex gap-2">
          <span class="p-2 border border-gray-200 rounded rounded-lg flex items-center gap-2">
            <Icon icon="bx:map" color="#f7bd62"></Icon>
            Jakarta, Indonesia
          </span>
          <span class="p-2 border border-gray-200 rounded rounded-lg flex items-center gap-2">
            <Icon icon="ic:outline-email" color="#f7bd62"></Icon>
            nabixka05@gmail.com
          </span>
          <span class="p-2 border border-gray-200 rounded rounded-lg flex items-center gap-2">
            <Icon icon="formkit:date" color="#f7bd62"></Icon>
            {{ umur() }} Tahun
          </span>
        </div>
        <div>
          <Icon width="35" icon="mdi:github" />
        </div>
      </div>
      <img src="/src/assets/goku.png" class="w-1/3 h-90 w-85 rounded-lg shadow-lg shadow-gray-900">
    </div>
  </section>

  <section class="min-h-screen bg-gray-100/50 pl-20 flex flex-col gap-15 pr-20">

    <!-- Keahlian -->
    <div>
      <span class="flex font-bold items-center justify-center pt-5 gap-3 text-2xl">
        <Icon icon="mdi:code" color="#f7bd62" width="25"></Icon>Keahlian Saya
      </span>

      <div class="grid grid-cols-2 items-start gap-5">
        <!-- Main -->
        <div class="flex flex-col items-center justify-center">
          <h3 class="text-xl font-semibold">Main</h3>
          <div class="grid grid-cols-5 flex gap-5 pt-2">
            <div v-for="m in Keahlian.main" :key="m.name"
              class="flex flex-col items-center justify-between bg-white shadow-lg p-3 rounded-lg w-25 h-30">
              <div class="flex flex-1 items-center justify-center">
                <img class="h-12 w-12 object-contain" :src="m.img" :alt="m.name">
              </div>
              <p class="mt-2 text-center text-sm font-medium text-gray-700">{{ m.name }}</p>
            </div>
          </div>
        </div>

        <!-- Learning -->
        <div class="flex flex-col items-center justify-center">
          <h3 class="text-xl font-semibold">Learning</h3>
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
      <div class="border-2 rounded-lg p-3 border-blue-200 bg-blue-100">
        <span class="flex items-center gap-2 text-xl font-bold">
          <Icon icon="mdi:like-outline" width="30" color="#f7bd62"></Icon> Kelebihan
        </span>
        <div class="flex flex-col gap-1 pt-3">
          <span class="flex items-center gap-2" v-for="s in sw.str">
            <Icon width="25" icon="ei:check"></Icon>{{ s.value }}
          </span>
        </div>
      </div>
      <div class="border-2 rounded-lg p-3 border-red-200 bg-linear-to-r from-red-200/90 to-red-100">
        <span class="flex items-center gap-2 text-xl font-bold">
          <Icon icon="mdi:dislike-outline" width="30" color="#f7bd62"></Icon> Kekurangan
        </span>
        <div class="flex flex-col gap-1 pt-3">
          <span class="flex items-center gap-2" v-for="w in sw.weak">
            <Icon width="20" icon="meteor-icons:circle-xmark"></Icon>{{ w.value }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>