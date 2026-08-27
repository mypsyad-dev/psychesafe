<template>
  <div class="bg-background rounded-lg p-4 border border-border">
    <div class="flex items-center justify-between mb-2">
      <span class="font-medium text-foreground">{{ name }}</span>
      <span class="text-sm text-muted-foreground">{{ level }}%</span>
    </div>
    <div class="w-full bg-muted rounded-full h-2 overflow-hidden">
      <div
        class="h-full rounded-full transition-all duration-1000 ease-out"
        :class="gradientClass"
        :style="{ width: `${displayedLevel}%` }"
      ></div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue'

const props = defineProps({
  name: { type: String, required: true },
  level: { type: Number, required: true },
  color: { type: String, default: 'primary' },
})

const displayedLevel = ref(0)

const gradientClass = computed(() =>
  props.color === 'primary'
    ? 'bg-gradient-to-r from-blue-500 to-violet-500'
    : 'bg-gradient-to-r from-pink-500 to-rose-500'
)

onMounted(() => {
  setTimeout(() => {
    displayedLevel.value = props.level
  }, 100)
})
</script>

<style scoped>
</style>