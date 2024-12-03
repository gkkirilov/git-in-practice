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
  <div class="relative w-full max-w-4xl mx-auto">
    <!-- Truck Container -->
    <div class="border-2 border-gray-800 rounded-lg p-4">
      <!-- Cab Section -->
      <div class="bg-gray-200 h-32 rounded-lg flex items-center justify-center mb-2">
        <div class="text-center">
          <span class="font-bold">Cab</span>
        </div>
      </div>
      
      <!-- Cargo Area -->
      <div class="bg-white border-2 border-gray-400 h-64 rounded-lg p-4">
        <!-- Cargo Sections -->
        <div class="grid grid-cols-3 gap-4 h-full">
          <template v-for="section in cargoSections" :key="section.id">
            <div 
              class="border border-dashed border-gray-400 rounded p-2 flex items-center justify-center cursor-pointer hover:bg-gray-50"
              @click="handleSectionClick(section)"
            >
              <span class="text-sm">{{ section.label }}</span>
            </div>
          </template>
        </div>
      </div>

      <!-- Wheels -->
      <div class="flex justify-between mt-2">
        <div class="flex gap-4">
          <div class="w-8 h-8 bg-gray-800 rounded-full"></div>
          <div class="w-8 h-8 bg-gray-800 rounded-full"></div>
        </div>
        <div class="flex gap-4">
          <div class="w-8 h-8 bg-gray-800 rounded-full"></div>
          <div class="w-8 h-8 bg-gray-800 rounded-full"></div>
        </div>
      </div>
    </div>
  </div>
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

const cargoSections = ref([
  { id: 1, label: 'Section 1', status: 'empty' },
  { id: 2, label: 'Section 2', status: 'empty' },
  { id: 3, label: 'Section 3', status: 'empty' },
  { id: 4, label: 'Section 4', status: 'empty' },
  { id: 5, label: 'Section 5', status: 'empty' },
  { id: 6, label: 'Section 6', status: 'empty' },
])

const emit = defineEmits(['section-click'])

const handleSectionClick = (section) => {
  emit('section-click', section)
}
</script>
