<template>
  <div class="pt-20">
    <!-- Back link -->
    <div class="container-tight pt-8">
      <RouterLink to="/" class="inline-flex items-center gap-2 text-sm text-muted-foreground hover:text-primary transition-colors">
        <ArrowLeft class="h-4 w-4" />
        Back to Home
      </RouterLink>
    </div>

    <!-- Project content -->
    <article class="container-tight py-12">
      <!-- Project image -->
      <div class="relative rounded-2xl overflow-hidden mb-8">
        <img
          v-if="project"
          :src="project.image"
          :alt="project.title"
          class="w-full aspect-video object-cover"
        />
      </div>

      <!-- Title and tags -->
      <div class="mb-8">
        <h1 class="text-4xl md:text-5xl font-display font-bold mb-4">
          {{ project?.title || 'Project not found' }}
        </h1>
        <div class="flex flex-wrap gap-2 mb-4">
          <span
            v-for="tag in project?.tags"
            :key="tag"
            class="text-sm px-3 py-1 bg-muted rounded-full text-muted-foreground"
          >
            {{ tag }}
          </span>
        </div>
      </div>

      <!-- Description -->
      <div class="grid md:grid-cols-3 gap-12">
        <div class="md:col-span-2">
          <h2 class="text-2xl font-display font-semibold mb-4">About this project</h2>
          <p class="text-muted-foreground mb-6 leading-relaxed">
            {{ project?.description || 'No description available.' }}
          </p>

          <p class="text-muted-foreground leading-relaxed">
            This project was built with a focus on performance, accessibility, and a clean user experience. The architecture is modular and scalable, with reusable components and a strong emphasis on best practices.
          </p>
        </div>

        <!-- Sidebar -->
        <aside class="space-y-6">
          <div class="bg-card border border-border rounded-xl p-6">
            <h3 class="font-semibold mb-4">Project Info</h3>
            <div class="space-y-3 text-sm">
              <div class="flex justify-between">
                <span class="text-muted-foreground">Role</span>
                <span>Lead Developer</span>
              </div>
              <div class="flex justify-between">
                <span class="text-muted-foreground">Year</span>
                <span>2026</span>
              </div>
              <div class="flex justify-between">
                <span class="text-muted-foreground">Status</span>
                <span class="text-green-500">Live</span>
              </div>
            </div>
          </div>

          <div v-if="project" class="flex flex-col gap-3">
            <a
              v-if="project.demoUrl"
              :href="project.demoUrl"
              target="_blank"
              rel="noopener noreferrer"
              class="btn btn-primary justify-center"
            >
              <ExternalLink class="h-4 w-4" />
              Live Demo
            </a>
            <a
              v-if="project.githubUrl"
              :href="project.githubUrl"
              target="_blank"
              rel="noopener noreferrer"
              class="btn btn-ghost justify-center"
            >
              <Github class="h-4 w-4" />
              Source Code
            </a>
          </div>
        </aside>
      </div>
    </article>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useRoute, RouterLink } from 'vue-router'
import { ArrowLeft, ExternalLink, Github } from 'lucide-vue-next'

const route = useRoute()

const projects = [
  {
    id: 1,
    title: 'E-commerce Platform',
    description:
      'A full-featured e-commerce platform built with Vue 3, Pinia, and Stripe integration. Features include real-time inventory, user authentication, and a powerful admin dashboard.',
    image:
      'https://images.unsplash.com/photo-1557821752-0f4e39367e98?w=1200&auto=format&fit=crop&q=80',
    tags: ['Vue 3', 'TypeScript', 'Tailwind CSS', 'Stripe'],
    demoUrl: 'https://demo.example.com',
    githubUrl: 'https://github.com',
  },
  {
    id: 2,
    title: 'Dashboard Application',
    description:
      'Real-time analytics dashboard with WebSocket integration and charting. Built to handle thousands of concurrent users with sub-second response times.',
    image:
      'https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=1200&auto=format&fit=crop&q=80',
    tags: ['Vue 3', 'Chart.js', 'WebSocket'],
    demoUrl: 'https://demo.example.com',
    githubUrl: 'https://github.com',
  },
  {
    id: 3,
    title: 'Weather App',
    description:
      'Beautiful weather application with API integration and offline support. Uses service workers for full PWA capabilities.',
    image:
      'https://images.unsplash.com/photo-1504608524839-e30b8e63b4a0?w=1200&auto=format&fit=crop&q=80',
    tags: ['Vue 3', 'OpenWeather API', 'PWA'],
    demoUrl: 'https://demo.example.com',
    githubUrl: 'https://github.com',
  },
]

const project = computed(() => projects.find((p) => p.id === Number(route.params.id)))
</script>

<style scoped>
</style>