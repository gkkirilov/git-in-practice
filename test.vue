<template>
  <header class="bg-slate-900 text-white">
    <!-- Top Bar -->
    <div class="bg-slate-800 py-2">
      <div class="container mx-auto px-4 flex justify-between items-center text-sm">
        <div class="flex gap-4">
          <span class="flex items-center gap-2">
            <Icon name="ph:phone" />
            (555) 123-4567
          </span>
          <span class="flex items-center gap-2">
            <Icon name="ph:envelope" />
            info@truckcompany.com
          </span>
        </div>
        <div class="flex gap-4">
          <a href="#" class="hover:text-yellow-400">Dealer Login</a>
          <a href="#" class="hover:text-yellow-400">Support</a>
        </div>
      </div>
    </div>

    <!-- Main Header -->
    <div class="container mx-auto px-4 py-4">
      <nav class="flex justify-between items-center">
        <!-- Logo -->
        <NuxtLink to="/" class="text-2xl font-bold">
          TRUCK<span class="text-yellow-400">CO</span>
        </NuxtLink>

        <!-- Navigation -->
        <div class="hidden md:flex gap-8">
          <NuxtLink 
            v-for="item in navItems" 
            :key="item.path"
            :to="item.path"
            class="hover:text-yellow-400 transition-colors"
          >
            {{ item.label }}
          </NuxtLink>
        </div>

        <!-- CTA Button -->
        <NuxtLink 
          to="/contact" 
          class="bg-yellow-400 text-slate-900 px-6 py-2 rounded-md font-semibold hover:bg-yellow-500 transition-colors"
        >
          Get a Quote
        </NuxtLink>

        <!-- Mobile Menu Button -->
        <button class="md:hidden" @click="isMenuOpen = !isMenuOpen">
          <Icon name="ph:list-bold" size="24" />
        </button>
      </nav>
    </div>

    <!-- Mobile Menu -->
    <div 
      v-show="isMenuOpen" 
      class="md:hidden bg-slate-800 absolute w-full z-50"
    >
      <div class="container mx-auto px-4 py-4">
        <NuxtLink 
          v-for="item in navItems" 
          :key="item.path"
          :to="item.path"
          class="block py-2 hover:text-yellow-400 transition-colors"
        >
          {{ item.label }}
        </NuxtLink>
      </div>
    </div>
  </header>
</template>

<script setup>
const isMenuOpen = ref(false)

const navItems = [
  { label: 'Home', path: '/' },
  { label: 'Trucks', path: '/trucks' },
  { label: 'Services', path: '/services' },
  { label: 'Parts', path: '/parts' },
  { label: 'About', path: '/about' },
]
</script>
