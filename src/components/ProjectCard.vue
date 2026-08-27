<template>
  <div class="group relative flex flex-col h-full bg-card border border-border rounded-xl shadow-lg overflow-hidden transition-all duration-300 hover:shadow-2xl hover:-translate-y-1">
    <!-- Image -->
    <div class="relative overflow-hidden aspect-video">
      <img
        :src="project.image"
        :alt="project.title"
        class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
      />
      <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>

      <!-- Featured badge -->
      <div
        v-if="project.featured"
        class="absolute top-3 right-3 bg-primary text-primary-foreground text-xs font-semibold px-2.5 py-1 rounded-full"
      >
        Featured
      </div>
    </div>

    <!-- Content -->
    <div class="p-6 flex flex-col flex-1">
      <h3 class="text-xl font-display font-bold text-foreground mb-2">{{ project.title }}</h3>
      <p class="text-sm text-muted-foreground mb-4 flex-1">{{ project.description }}</p>

      <!-- Tags -->
      <div class="flex flex-wrap gap-2 mb-4">
        <span
          v-for="tag in project.tags"
          :key="tag"
          class="text-xs px-2.5 py-1 bg-muted rounded-full text-muted-foreground"
        >
          {{ tag }}
        </span>
      </div>

      <!-- Actions -->
      <div class="flex items-center justify-between pt-4 border-t border-border">
        <a
          :href="project.demoUrl"
          target="_blank"
          rel="noopener noreferrer"
          class="flex items-center gap-2 text-sm font-medium text-primary hover:text-primary/80 transition-colors"
        >
          <Eye class="h-4 w-4" />
          Live Demo
        </a>
        <a
          :href="project.githubUrl"
          target="_blank"
          rel="noopener noreferrer"
          class="flex items-center gap-2 text-sm font-medium text-muted-foreground hover:text-foreground transition-colors"
        >
          <Github class="h-4 w-4" />
          Source
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Eye, Github } from 'lucide-vue-next'

const props = defineProps({
  project: {
    type: Object,
    required: true,
  },
})
</script>

<style scoped>
</style>