<script setup>
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'

import NavItem from './NavItem.vue'

const navItems = {
  activities: ListBulletIcon,
  progress: ChartBarIcon,
  today: ClockIcon,
}
</script>

<template>
  <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="flex items-center justify-around border-t">
      <NavItem v-for="(navIcon, navItem) in navItems" :key="navItem" :href="`#${navItem}`">
        <component :is="navIcon" class="h-6 w-6" />
        {{ navItem }}
      </NavItem>
    </ul>
  </nav>
</template>
