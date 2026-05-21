<script setup>
import { Link } from '@inertiajs/vue3';
import { onMounted, ref } from 'vue';
const isOpen = ref(false)


const menuItems=[
    {name: 'Home', path: '/'},
    {name: 'About', path: route('client.about')},
    {name: 'Services', path: '#'},
    {name: 'Gallery', path: '#'},
    {name: 'Contact', path: '#'}
]
// const isActive = (path) => {
//   return route.path === path
//     ? 'text-yellow-300 font-semibold'
//     : 'hover:text-yellow-200'
// }

const newsText=ref(
      'Nepal launches new IT policy • Vue 3 becomes more powerful • Tailwind CSS is trending • Developers love modern UI • New tech updates coming soon •'
)

</script>
<template>
    <nav class="bg-blue-600 text-white shadow-lg">
       <div class="max-w-7xl mx-auto px-4">
        <div class="flex justify-between items-center h-16">
            <!-- Logo -->
             <div class="text-2xl font-bold">
                MyLogo
             </div>
             <!-- Desktop Menu -->
              <div class="hidden sm:flex space-x-8">
                <Link v-for="item in menuItems"
                :key="item.name"
                :href="item.path"
                class=" transition"
                
                >
                {{ item.name }}
              </Link>
              </div>

              <!-- Mobile Menu Button -->
               <button 
               @click="isOpen = !isOpen"
               class="md:hidden text-3xl"
               >
               <i class="bi" :class="isOpen ? ' bi-x-lg' : ' bi-list'"></i>
               </button>
        </div>
       </div>

       <!-- Mobile Menu -->

       <div
       v-if="isOpen"
       class="md:hidden bg-blue-700"
       >
       <Link
       v-for="item in menuItems"
       :key="item.name"
       :href="item.path"
       class="block px-4 py-3 transition"
       
       @click="isOpen=false"
       >
       {{ item.name }}
      </Link>
       </div>
    </nav>
    <!-- news ticker -->
     <div class="bg-red-600 text-white overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 py-2 flex items-center">

            <!-- label -->
             <span class font-bold  whitespace-nowrap>
                 Breaking <br> News:
             </span>

            <!-- scrolling text  -->
             <div class="overflow-hidden w-full">
                <div class="  animate-scroll  text-sm">
                    {{ newsText }}
                </div>
             </div>
        </div>
     </div>
</template>
<style scoped>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css");
@keyframes scroll {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(-100%);
  }
}

.animate-scroll {
  display: inline-block;
  white-space: nowrap;
  animation: scroll 12s linear infinite;
}
</style>