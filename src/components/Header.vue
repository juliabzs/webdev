<script setup>
import { Menu, X } from 'lucide-vue-next';
import { ref } from 'vue';

const isMenuOpen = ref(false)

const menuItems = [
  { name: 'Education', href: '#education' },
  { name: 'Certificates', href: '#certificates' },
  { name: 'About', href: '#about' },
  { name: 'Skill', href: '#skills' },
  { name: 'Projects', href: '#projects' }

]

const scrollToSection = (href) => {
  isMenuOpen.value = false
  const element = document.querySelector(href)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<template>
  <header class="relative z-50 px-6 py-7">
    <div class="max-w-7xl mx-auto flex justify-between items-center">
      <!-- Logo -->
      <div class="text-white text-3xl font-black cursor-pointer">
        WEBDEV<span class="text-primary">.</span>
      </div>

      <!-- Navigation Desktop -->
      <nav class="hidden md:flex items-center gap-8">
        <ul class="flex gap-8">
          <li v-for="item in menuItems" :key="item.name">
            <button
              @click="scrollToSection(item.href)"
              class="text-primary hover:text-white text-base font-medium transition-colors"
            >
              {{ item.name }}
            </button>
          </li>
        </ul>
        <button
          @click="scrollToSection('#contact')"
          class="bg-primary hover:bg-primary/90 text-white px-6 py-2.5 rounded-lg text-base font-semibold transition-all"
        >
          Contate-me
        </button>
      </nav>

      <!-- Menu Button Mobile -->
      <button
        class="md:hidden text-white"
        @click="isMenuOpen = !isMenuOpen"
      >
        <Menu v-if="!isMenuOpen" :size="32" />
        <X v-else :size="32" />
      </button>
    </div>

    <!-- Overlay Mobile -->
    <div
      v-if="isMenuOpen"
      class="fixed inset-0 bg-black/60 backdrop-blur-sm md:hidden"
      @click="isMenuOpen = false"
    ></div>

    <!-- Drawer Mobile -->
    <div
      class="fixed top-0 right-0 h-full w-80 bg-[#111827] p-4
      z-50 transform transition-transform duration-300 md:hidden flex flex-col"
      :class="isMenuOpen ? 'translate-x-0' : 'translate-x-full'"
    >
      <button
        class="self-end text-white mb-10"
        @click="isMenuOpen = false"
      >
        <X :size="32" />
      </button>

      <ul class="flex flex-col gap-8">
        <li v-for="item in menuItems" :key="item.name">
          <button
            @click="scrollToSection(item.href)"
            class="text-white text-xl font-semibold 
            hover:text-primary transition-colors"
          >
            {{ item.name }}
          </button>
        </li>
        <li class="pt-6">
          <button
            @click="scrollToSection('#contact')"
            class="w-full bg-primary text-white py-4 rounded-xl text-lg font-bold"
          >
            Contate-me
          </button>
        </li>
      </ul>
    </div>
  </header>
</template>
