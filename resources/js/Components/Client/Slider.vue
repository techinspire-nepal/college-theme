<script setup>
import { onMounted, ref } from 'vue';
import video from "@/assets/video.mp4"

</script>
<template>

     <!-- Carousel -->

   <section class="relative h-screen overflow-hidden">
  <video
  autoplay
  muted
  loop
  playsinline
  class="absolute top-1/2 left-1/2 w-full h-full object-cover -translate-x-1/2 -translate-y-1/2 z-[-2]"
>
  <source src="@/assets/college.mp4" type="video/mp4" />
</video>
  <!-- Overlay -->
    <div class="absolute inset-0 bg-black/60"></div>

    <!-- Content -->
    <div
      class="relative z-10 flex flex-col justify-center items-center text-white text-center h-full px-4"
    >

      <h1 class="text-4xl md:text-6xl font-bold mb-6 animate-fadeIn">
        Welcome To Our Website
      </h1>

      <p class="text-lg md:text-2xl mb-8 max-w-2xl text-gray-200">
        Empowering students with knowledge, creativity and leadership for a brighter future.
      </p>

      <div class="flex flex-wrap justify-center gap-4">

        <button
          class="bg-yellow-400 hover:bg-yellow-500 text-black px-8 py-4 rounded-xl font-semibold transition duration-300"
        >
          Explore More
        </button>

        <button
          class="border border-white hover:bg-white hover:text-black px-8 py-4 rounded-xl font-semibold transition duration-300"
        >
          Contact Us
        </button>

      </div>
    </div>
  
</section>   
  
</template>
<style scoped>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css");

</style>