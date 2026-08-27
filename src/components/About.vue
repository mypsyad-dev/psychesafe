<template>
  <section id="about" class="section">
    <div class="container-tight">
      <h2 class="text-4xl font-display font-bold text-center mb-12">
        About <span class="text-primary">Me</span>
      </h2>

      <div class="grid md:grid-cols-2 gap-12 items-center">
        <!-- Profile Image -->
        <div class="relative">
          <div class="absolute -inset-4 bg-gradient-to-br from-primary/20 to-purple-500/20 rounded-3xl blur-2xl"></div>
          <img
            :src="profileImage"
            alt="Profile photo of Psyche Safe"
            class="relative w-full max-w-sm rounded-2xl shadow-2xl object-cover"
          />
        </div>

        <!-- Content -->
        <div>
          <h3 class="text-2xl font-display font-semibold mb-4">
            Frontend Developer with a Designer's Eye
          </h3>

          <p class="text-base text-muted-foreground mb-6 leading-relaxed">
            I've been building for the web for 15 years — long enough to have shipped through jQuery, the rise of single-page apps, and the slow return of "just write good HTML and CSS." I specialize in Vue, and I bring a graphic and web design background to the table. That dual lens matters: I tend to be precise in transforming designs into interfaces — if the spec says 8 pixels of padding, the interface has 8 pixels of padding.
          </p>

          <p class="text-base text-muted-foreground mb-6 leading-relaxed">
            Coding is still where I do my best thinking, so I'm not in a rush to leave it. But I don't close doors — if a lead role comes along where I can level up alongside the team, I'd take that call. Outside of work, you'll usually find me on my 110cc bike. It's the best place I know to think through a hard problem.
          </p>

          <div class="flex flex-wrap items-center gap-4 mb-8">
            <div class="flex items-center gap-2">
              <CheckCircle class="h-5 w-5 text-green-500" />
              <span class="text-sm">Specialty: Vue & design-to-code</span>
            </div>
            <div class="flex items-center gap-2">
              <CheckCircle class="h-5 w-5 text-green-500" />
              <span class="text-sm">Open to lead opportunities</span>
            </div>
          </div>

          <!-- Stats -->
          <div class="grid grid-cols-3 gap-6">
            <div class="text-center">
              <div class="text-3xl font-bold text-primary mb-1">15+</div>
              <div class="text-xs text-muted-foreground uppercase tracking-wider">Years Building</div>
            </div>
            <div class="text-center">
              <div class="text-3xl font-bold text-primary mb-1">Vue</div>
              <div class="text-xs text-muted-foreground uppercase tracking-wider">Core Specialty</div>
            </div>
            <div class="text-center">
              <div class="text-3xl font-bold text-primary mb-1">110cc</div>
              <div class="text-xs text-muted-foreground uppercase tracking-wider">Weekend Sidecar</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { CheckCircle } from 'lucide-vue-next'

const profileImage = '/profile.jpg'
</script>

<style scoped>
</style>