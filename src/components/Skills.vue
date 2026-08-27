<template>
  <section id="skills" class="section bg-muted">
    <div class="container-tight">
      <h2 class="text-4xl font-display font-bold text-center mb-12">
        Skills <span class="text-primary">I'm Skilled In</span>
      </h2>

      <div class="grid md:grid-cols-2 gap-8">
        <!-- Frontend Technologies -->
        <div>
          <h3 class="text-2xl font-display font-semibold mb-8">Frontend Mastery</h3>

          <div class="space-y-3">
            <skill-item
              v-for="item in frontendSkills"
              :key="item.name"
              :name="item.name"
              :level="item.level"
              :color="item.color"
            />
          </div>
        </div>

        <!-- Design & Tools -->
        <div>
          <h3 class="text-2xl font-display font-semibold mb-8">Design & Tools</h3>

          <div class="space-y-3">
            <skill-item
              v-for="item in designSkills"
              :key="item.name"
              :name="item.name"
              :level="item.level"
              :color="item.color"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import SkillItem from '@/components/SkillItem.vue'

const frontendSkills = [
  {
    name: "Vue 3 & Composition API",
    level: 95,
    color: "primary",
  },
  {
    name: "TypeScript",
    level: 90,
    color: "primary",
  },
  {
    name: "Vite",
    level: 92,
    color: "primary",
  },
  {
    name: "Pinia",
    level: 88,
    color: "primary",
  },
  {
    name: "Vue Router",
    level: 90,
    color: "primary",
  },
  {
    name: "Sass / SCSS",
    level: 85,
    color: "primary",
  },
  {
    name: "HTML5 / CSS3",
    level: 92,
    color: "primary",
  },
  {
    name: "Web Accessibility (a11y)",
    level: 88,
    color: "primary",
  },
]

const designSkills = [
  {
    name: "Figma",
    level: 82,
    color: "secondary",
  },
  {
    name: "Responsive Design",
    level: 95,
    color: "secondary",
  },
  {
    name: "Component Architecture",
    level: 93,
    color: "secondary",
  },
  {
    name: "CSS Animations",
    level: 85,
    color: "secondary",
  },
  {
    name: "Performance Optimization",
    level: 90,
    color: "secondary",
  },
  {
    name: "Jest / Vitest",
    level: 78,
    color: "secondary",
  },
  {
    name: "Git / Version Control",
    level: 90,
    color: "secondary",
  },
]
</script>

<style scoped>
</style>