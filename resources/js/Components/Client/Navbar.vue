<script setup>
import { Link } from "@inertiajs/vue3";
import { onMounted, ref } from "vue";
const isOpen = ref(false);

const menuItems = [
    { name: "Home", path: "/" },
    { name: "About", path: route("client.about") },
    { name: "Research", path: "#" },
    { name: "Projects", path: "#" },
    { name: "Events", path: "#" },
    { name: "News", path: "#" },
    { name: "Contact", path: "#" },
];
// const isActive = (path) => {
//   return route.path === path
//     ? 'text-yellow-300 font-semibold'
//     : 'hover:text-yellow-200'
// }

const newsText = ref(
    "Nepal launches new IT policy • Vue 3 becomes more powerful • Tailwind CSS is trending • Developers love modern UI • New tech updates coming soon •",
);
</script>
<template>
   <!-- TOP BAR -->
  <div class="bg-blue-900 text-white text-sm py-2">
    <div class="max-w-7xl mx-auto px-4 flex justify-between">
      <div>
        Navajeevan College of Nursing and Health Sciences
      </div>

      <div class="space-x-4">
        <a href="#" class="hover:text-yellow-300">Publications</a>
        <a href="#" class="hover:text-yellow-300">Downloads</a>
        <a href="#" class="hover:text-yellow-300">Contact</a>
      </div>
    </div>
  </div>
    <!-- NAVBAR -->
  <header class="bg-white shadow-md sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-4">
      <div class="flex justify-between items-center py-4">

        <!-- Logo -->
        <div class="flex items-center gap-4">
          <img src="@/assets/logoschool.png"
               class="h-16">

          <div>
            

            <p class="text-sm text-gray-500">
              Navajeevan College of Nursing and Health Sciences
            </p>
          </div>
        </div>

        <!-- Menu -->
        <nav class="hidden md:flex space-x-8 font-medium">
          <!-- Desktop Menu -->
        <div class="hidden md:flex space-x-8 ">
          <RouterLink
            v-for="item in menuItems"
            :key="item.name"
            :to="item.path"
            class="transition hover:text-blue-700 cursor-pointer"
          >
            {{ item.name }}
          </RouterLink>
        </div>
         <!-- Mobile Menu Button -->
        <button @click="isOpen = !isOpen" class="md:hidden text-3xl">
          <i class="bi" :class="isOpen ? ' bi-x-lg' : ' bi-list'"></i>
        </button>
        <!-- Mobile Menu -->

    <div v-if="isOpen" class="md:hidden bg-blue-700">
      <RouterLink
        v-for="item in menuItems"
        :key="item.name"
        :to="item.path"
        class="block px-4 py-3 transition"
        @click="isOpen = false"
      >
        {{ item.name }}
      </RouterLink>
    </div>
        </nav>

      </div>
    </div>
  </header>
    <!-- news ticker -->
    <div class="bg-red-600 text-white overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 py-2 flex items-center">
            <!-- label -->
            <span class font-bold whitespace-nowrap>
                Breaking <br />
                News:
            </span>

            <!-- scrolling text  -->
            <div class="overflow-hidden w-full">
                <div class="animate-scroll text-sm">
                    {{ newsText }}
                </div>
            </div>
        </div>
    </div>
</template>
<style scoped>
/* Top of your CSS file */
@import url('https://googleapis.com');

 body{
      font-family: 'Poppins', sans-serif;
    }

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
