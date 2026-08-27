<template>
  <section class="relative min-h-screen flex items-center justify-center overflow-hidden pt-20">
    <!-- Background elements -->
    <div class="absolute inset-0 -z-10">
      <div class="absolute inset-0 grid-bg"></div>
      <div class="absolute top-1/4 -left-1/4 w-96 h-96 bg-primary/10 rounded-full blur-3xl"></div>
      <div class="absolute bottom-1/4 -right-1/4 w-96 h-96 bg-purple-500/10 rounded-full blur-3xl"></div>
    </div>

    <div class="container-tight text-center relative z-10">
      <!-- Status badge -->
      <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-muted border border-border mb-8">
        <span class="relative flex h-2.5 w-2.5">
          <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-75"></span>
          <span class="relative inline-flex rounded-full h-2.5 w-2.5 bg-green-500"></span>
        </span>
        <span class="text-sm text-muted-foreground">Available for new projects</span>
      </div>

      <!-- Heading -->
      <h1 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-display font-bold mb-6 tracking-tight">
        <span class="text-foreground">Hi, I'm</span>
        <br />
        <span class="gradient-text">Psyche Safe</span>
      </h1>

      <!-- Subtitle -->
      <p class="text-xl md:text-2xl text-muted-foreground max-w-2xl mx-auto mb-10">
        I turn product ideas into fast, accessible web apps — usually with Vue, sometimes with a strong opinion about CSS.
      </p>

      <!-- CTA buttons -->
      <div class="flex flex-col sm:flex-row items-center justify-center gap-4">
        <a href="#projects" class="btn btn-primary px-8 py-3 text-base">
          View My Work
          <ArrowDown class="h-4 w-4" />
        </a>
        <a href="#contact" class="btn btn-ghost px-8 py-3 text-base">
          Get In Touch
        </a>
      </div>

      <!-- Social links -->
      <div class="flex items-center justify-center gap-4 mt-12">
        <a
          v-for="social in socials"
          :key="social.name"
          :href="social.url"
          target="_blank"
          rel="noopener noreferrer"
          :aria-label="social.name"
          class="p-3 rounded-full border border-border text-muted-foreground hover:text-foreground hover:border-primary/50 hover:bg-muted transition-all duration-200"
        >
          <component :is="social.icon" class="h-5 w-5" />
        </a>
      </div>

      <!-- Scroll indicator -->
      <div class="absolute bottom-10 left-1/2 -translate-x-1/2 animate-bounce">
        <a href="#about" aria-label="Scroll to about section">
          <Mouse class="h-6 w-6 text-muted-foreground" />
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ArrowDown, Mouse, Github, Linkedin, Twitter, Mail } from 'lucide-vue-next'

const socials = [
  { name: 'GitHub', url: 'https://github.com/mypsyad', icon: Github },
  { name: 'LinkedIn', url: 'https://linkedin.com/in/psychesafe', icon: Linkedin },
  { name: 'Email', url: 'mailto:safepsyche@gmail.com', icon: Mail },
]
</script>

<style scoped>
</style>