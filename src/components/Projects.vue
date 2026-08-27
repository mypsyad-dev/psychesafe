<template>
  <section id="projects" class="section">
    <div class="container-tight">
      <h2 class="text-4xl font-display font-bold text-center mb-12">
        Featured <span class="text-primary">Projects</span>
      </h2>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <project-card
          v-for="project in projects"
          :key="project.id"
          :project="project"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import ProjectCard from '@/components/ProjectCard.vue'

const projects = [
  {
    id: 1,
    title: "E-commerce Platform",
    description:
      "A full-featured e-commerce platform with Vue 3, Pinia, and Stripe integration",
    image:
      "https://images.unsplash.com/photo-1557821752-0f4e39367e98?w=800&auto=format&fit=crop&q=80",
    tags: ["Vue 3", "TypeScript", "Tailwind CSS", "Stripe"],
    demoUrl: "https://demo.example.com",
    githubUrl: "https://github.com",
    featured: true,
  },
  {
    id: 2,
    title: "Dashboard Application",
    description:
      "Real-time analytics dashboard with WebSocket integration and charting",
    image:
      "https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=800&auto=format&fit=crop&q=80",
    tags: ["Vue 3", "Chart.js", "WebSocket", "WebSockets"],
    demoUrl: "https://demo.example.com",
    githubUrl: "https://github.com",
    featured: false,
  },
  {
    id: 3,
    title: "Weather App",
    description:
      "Beautiful weather application with API integration and offline support",
    image:
      "https://images.unsplash.com/photo-1504608524839-e30b8e63b4a0?w=800&auto=format&fit=crop&q=80",
    tags: ["Vue 3", "OpenWeather API", "PWA", "Geolocation"],
    demoUrl: "https://demo.example.com",
    githubUrl: "https://github.com",
    featured: true,
  },
  {
    id: 4,
    title: "Recipe Finder",
    description:
      "Recipe sharing app with search, filtering, and user-generated content",
    image:
      "https://images.unsplash.com/photo-1495621369058-d00e881fbad8?w=800&auto=format&fit=crop&q=80",
    tags: ["Vue 3", "Firebase", "Material Design"],
    demoUrl: "https://demo.example.com",
    githubUrl: "https://github.com",
    featured: false,
  },
  {
    id: 5,
    title: "Fitness Tracker",
    description:
      "Mobile-first fitness tracking application with workout plans",
    image:
      "https://images.unsplash.com/photo-1476480862784-a5d9c0925ddf?w=800&auto=format&fit=crop&q=80",
    tags: ["Vue 3", "Ionitron", "Charts"],
    demoUrl: "https://demo.example.com",
    githubUrl: "https://github.com",
    featured: false,
  },
]
</script>

<style scoped>
</style>