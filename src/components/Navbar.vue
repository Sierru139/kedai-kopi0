<template>
  <nav 
    :class="['fixed right-0 left-0 top-0 h-14 flex items-center justify-between md:px-20 px-5 md:mx-0 z-40 backdrop-blur-sm', isScrolled ? 'dot' : 'dotgone']"
  >
    <a href="#" class="font-bold italic text-2xl">
      <span>Kop</span>
      <span class="bg-clip-text text-transparent bg-gradient-to-l from-[#bfa890] to-[#a28567]">pi</span>
    </a>
    
    <div class="text-sm md:flex hidden gap-x-5">
      <a href="#home" class="hover:underline active:text-white">Home</a>
      <a href="#product" class="hover:underline active:text-white">Product</a>
      <a href="#about" class="hover:underline active:text-white">About Us</a>
      <a href="#contact" class="hover:underline active:text-white">Contact</a>
    </div>
    
    <div class="md:hidden flex">
      <button @click="toggleMobileMenu" class="border-black p-2 mr-3">
        <i class="fa fa-bars text-[#381546]"></i>
      </button>
      <div 
        v-show="mobileMenuOpen" 
        class="fixed p-2 navin gap-y-2 flex flex-col top-12 right-2 left-2 mt-3 text-lg bg-[#c6783fbf] rounded-md backdrop-blur text-center"
      >
        <a href="#home" class="hover:underline active:text-white" @click="toggleMobileMenu">Home</a>
        <a href="#product" class="hover:underline active:text-white" @click="toggleMobileMenu">Product</a>
        <a href="#about" class="hover:underline active:text-white" @click="toggleMobileMenu">About Us</a>
        <a href="#contact" class="hover:underline active:text-white" @click="toggleMobileMenu">Contact</a>
      </div>
    </div>
    
    <div class="md:flex hidden gap-x-6">
      <a href="#product">
        <i class="fas fas fa-shopping-cart"></i>
      </a>
      <a href="">
        <i class="fas fa-phone"></i>
      </a>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const mobileMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 60
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>
