<script setup>
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'
import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from '../constants.js'
import NavItem from './NavItem.vue'

defineProps(['currentPage'])

const emit = defineEmits(['navigate'])

const navItems = {
  [PAGE_TIMELINE]: ClockIcon,
  [PAGE_ACTIVITIES]: ListBulletIcon,
  [PAGE_PROGRESS]: ChartBarIcon,
}
</script>

<template>
  <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="flex items-center justify-around border-t">
      <NavItem
        v-for="(navIcon, navItem) in navItems"
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
