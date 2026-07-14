<script setup>
  import { Icon } from '@iconify/vue';
  
  const umur = () => {
    const birthDate = new Date('2008-12-27')
    const date = new Date()

    let umur = date.getFullYear() - birthDate.getFullYear()
    const bulan =  date.getMonth() - birthDate.getMonth()

    if(bulan < 0 || bulan === 0 && date.getDate() < birthDate.getDate()){
      umur--
    }
    
    return umur
  }
</script>

<template>

  <section class="text-white bg-linear-to-br from-gray-950/70 via-gray-800/70 to-gray-700/70 min-h-screen flex flex-col gap-15">
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
        <h5 class="flex items-center gap-1 text-lg font-semibold text-orange-400">Halo, <span class="text-orange-300 pr-1">Saya</span> <Icon icon="entypo:hand" color="#f7bd62"></Icon></h5>
        <h1 class="text-4xl font-bold">Muhammad Fadhil Abiprayana</h1>
        <h3 class="font-semibold text-2xl text-orange-400">Web Developer <span class="text-white">| Cloud Engineer</span></h3>
        <h6>Saya adalah seorang pelajar dan programmer yang memiliki semangat tinggi dalam dunia teknologi, khususnya dalam pengembangan web. Saya suka membangun aplikasi yang bermanfaat.</h6>
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
          <Icon width="35" icon="mdi:github"/>
        </div>
      </div>
      <img src="/src/assets/goku.png" class="w-1/3 h-90 w-85 rounded-lg shadow-lg shadow-gray-900">
    </div>
  </section>
</template>