<template>
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
