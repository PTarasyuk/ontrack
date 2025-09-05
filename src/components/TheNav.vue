<script setup>
import NavItem from './NavItem.vue'
import { NAV_ITEMS } from '@/constants'

defineProps(['currentPage'])

const emit = defineEmits(['navigate'])
</script>

<template>
  <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="flex items-center justify-around border-t">
      <NavItem
        v-for="(navIcon, navItem) in NAV_ITEMS"
        :key="navItem"
        :href="`#${navItem}`"
        :class="{ 'bg-gray-200 pointer-events-none': navItem === currentPage }"
        @click="emit('navigate', navItem)"
      >
        <component :is="navIcon" class="h-6 w-6" />
        {{ navItem }}
      </NavItem>
    </ul>
  </nav>
</template>
