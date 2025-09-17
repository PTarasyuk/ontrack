<script setup>
import { computed, ref } from 'vue'
import { HUNDRED_PERCENT } from '@/constants'
import { useSecondsSinceMidnight } from '@/composables/seconds-since-midnight'

const indicatorRef = ref()

const { secondsSinceMidnightPercentage } = useSecondsSinceMidnight()

const topOffset = computed(
  () => (secondsSinceMidnightPercentage.value * getTimelineHight()) / HUNDRED_PERCENT
)

function getTimelineHight() {
  return indicatorRef.value?.parentNode.getBoundingClientRect().height
}
</script>

<template>
  <hr
    ref="indicatorRef"
    class="pointer-events-none absolute z-10 w-full border-b-2 border-red-600"
    :style="{ top: `${topOffset}px` }"
  />
</template>
