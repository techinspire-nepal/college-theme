<script setup>
import { onMounted, ref } from 'vue';



/*=========== Carousel ========== */
const currentSlide=ref(0)

const slides=[
   {
    image:
      'https://images.unsplash.com/photo-1506744038136-46273834b3fb',
    title: 'Welcome To Our Website',
    description: 'Discover amazing experiences with us'
  },
  {
    image:
      'https://images.unsplash.com/photo-1493246318656-5bfd4cfb29b8',
    title: 'Creative Design',
    description: 'Modern UI with Tailwind CSS & Vue 3'
  },
  {
    image:
      'https://images.unsplash.com/photo-1519389950473-47ba0277781c',
    title: 'Build Your Future',
    description: 'Fast, responsive and beautiful websites'
  }
]

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length
}

/*================== Auto Slides ================= */

onMounted(() => {
  setInterval(() => {
    nextSlide()
  }, 4000)
   
})
</script>
<template>

     <!-- Carousel -->

   <section class="relative h-screen overflow-hidden">
  <video
    autoplay
    muted
    loop
    class="absolute top-0 left-0 w-full h-full object-cover"
  >
    <source src="video.mp4" type="video/mp4" />
    Your browser does not support the video tag.
  </video>
  <div class="absolute top-0 left-0 w-full h-full bg-black bg-opacity-50"></div>
  <div class="relative z-10 flex items-center justify-center h-full">
    <div class="text-center text-white px-4">
      <h1 class="text-5xl font-bold mb-4">Welcome to Our Website</h1>
      <p class="text-xl mb-6">Experience the best services with us</p>
      <a
        href="#"
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
      >
        Get Started
      </a>
    </div>
  </div>
</section>   
  
</template>
<style scoped>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css");

</style>