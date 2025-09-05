<script setup>
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'

const navItems = {
  activities: ListBulletIcon,
  progress: ChartBarIcon,
  today: ClockIcon,
}
</script>

<template>
  <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="flex items-center justify-around border-t">
      <li v-for="(navIcon, navItem) in navItems" :key="navItem" class="flex-1">
        <a :href="`#${navItem}`" class="flex flex-col items-center p-2 text-sm capitalize">
          <component :is="navIcon" class="h-6 w-6" />
          {{ navItem }}
        </a>
      </li>
    </ul>
  </nav>
</template>
