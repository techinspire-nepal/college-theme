<script setup>
import { onMounted, ref } from 'vue';
const isOpen = ref(false)


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

      <section class="relative w-full h-['500px'] bg-black overflow-hidden" >
        <div style="height:100vh">
        </div>
        <!-- slides -->
         <div v-for="(slide,index) in slides"
         :key="index"
         class="absolute h-['700px'] inset-0 transtion-opacite duration-700"
         :class="currentSlide === index ? 'opacity-100' : 'opacity-0'"
         >
         
         <!-- image -->
          <img 
          :src="slide.image"
          :alt="slide.title"
          class="w-full h-['100vh'] object-cover"
          />

          <!-- overlay -->
           <div class="absolute inset-0 bg-black/50"></div>

           <!-- content -->
            <div class="absolute inset-0 flex flex-col justify-center items-center text-white px-4">
              <h1 class="text-4xl md:text-6xl font-bold mb-4">
                {{ slide.title }}
              </h1>

              <p class="text-lg md:text-2xl mb-6">
                {{ slide.description }}
              </p>

              <button class="bg-yellow-400 hover:bg-yellow-500 text-black px-6 py-3 rounded-lg font-semibold transition">
                Explore More
              </button>
            </div>
         </div>

         <!-- Previous Button -->
          <button @click="prevSlide" 
          class="absolute left-4 top-1/2 -translate-y-1/2 bg-white/30 hover:bg-white/50 text-white p-3 rounded-full"
          >
          <i class="bi bi-chevron-left text-2xl"></i>
          </button>

          <!-- Next Button -->
           <button @click="nextSlide"
           class="absolute right-4 top-1/2 -translate-y-1/2 bg-white/30 hover:bg-white/50 text-white p-3 rounded-full"
           >
           <i class="bi bi-chevron-right text-2xl"></i>
           </button>

           <!-- Dots -->
            <div class="absolute bottom-5 left-1/2 -translate-x-1/2 flex space-x-3">
              <button
              v-for="(slide,index) in slides"
              :key="index"
              @click="currentSlide=index"
              class="w-3 h-3 rounded-full"
              :class="currentSlide === index ? 'bg-yellow-400' : 'bg-white'"
              >
              </button>
            </div>
      </section>
</template>
<style scoped>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css");

</style>