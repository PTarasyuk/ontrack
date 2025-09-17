<script setup>
import { computed, ref, onActivated, onDeactivated } from 'vue'
import { HUNDRED_PERCENT } from '@/constants'
import { secondsSinceMidnightPercentage, startTimer, stopTimer } from '@/time'

const indicatorRef = ref()

const topOffset = computed(
  () => (secondsSinceMidnightPercentage.value * getTimelineHight()) / HUNDRED_PERCENT
)

function getTimelineHight() {
  return indicatorRef.value?.parentNode.getBoundingClientRect().height
}

onActivated(startTimer)
onDeactivated(stopTimer)
</script>

<template>
  <hr
    ref="indicatorRef"
    class="pointer-events-none absolute z-10 w-full border-b-2 border-red-600"
    :style="{ top: `${topOffset}px` }"
  />
</template>
