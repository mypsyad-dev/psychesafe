<template>
  <section id="projects" class="section">
    <div class="container-tight">
      <h2 class="text-4xl font-display font-bold text-center mb-4">
        Featured <span class="text-primary">Projects</span>
      </h2>
      <p class="text-center text-muted-foreground mb-16">
        A collection of things I've built
      </p>

      <!-- Coming Soon -->
      <div class="flex flex-col items-center justify-center gap-8 py-20 rounded-2xl border border-dashed border-border bg-muted/30">
        <!-- Animated icon -->
        <div class="relative flex items-center justify-center">
          <div class="absolute h-24 w-24 rounded-full bg-primary/10 animate-ping opacity-40"></div>
          <div class="relative flex h-20 w-20 items-center justify-center rounded-full bg-primary/10">
            <Hammer class="h-9 w-9 text-primary" />
          </div>
        </div>

        <!-- Text -->
        <div class="text-center max-w-md space-y-3">
          <h3 class="text-2xl font-display font-bold">Projects Coming Soon</h3>
          <p class="text-muted-foreground leading-relaxed">
            I'm currently curating my best work to showcase here.
            In the meantime, feel free to reach out — I'd love to
            collaborate or chat about what I'm building.
          </p>
        </div>

        <!-- CTA -->
        <a href="#contact" class="btn btn-primary gap-2">
          <Mail class="h-4 w-4" />
          Get in Touch
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Hammer, Mail } from 'lucide-vue-next'
</script>

<style scoped>
</style>