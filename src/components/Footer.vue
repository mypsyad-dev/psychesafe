<template>
  <footer class="border-t border-border">
    <div class="container-wide py-8 flex flex-col md:flex-row md:items-center md:justify-between gap-4">
      <div class="flex items-center gap-4 text-center md:text-left">
        <RouterLink to="/" class="flex items-center gap-2 text-xl font-display font-bold gradient-text">
          <img src="@/assets/logo.jpg" alt="Psyche Safe logo" class="h-7 w-7 rounded-lg" />
          Psyche Safe
        </RouterLink>
        <p class="text-sm text-muted-foreground">
          Building web experiences that matter
        </p>
      </div>

      <div class="flex items-center justify-center md:justify-end gap-6 text-sm">
        <!-- Navigation -->
        <div class="flex flex-wrap gap-6">
          <RouterLink
            v-for="link in footerLinks"
            :key="link"
            :to="link.href"
            class="hover:text-primary transition-colors text-muted-foreground"
          >
            {{ link.label }}
          </RouterLink>
        </div>

        <!-- Social -->
        <div class="flex gap-3">
          <a
            v-for="social in socials"
            :key="social.name"
            :href="social.url"
            target="_blank"
            rel="noopener noreferrer"
            :aria-label="social.name"
            class="p-2 rounded-full border border-border text-muted-foreground hover:text-primary hover:border-primary/50 hover:bg-muted transition-all duration-200"
          >
            <component :is="social.icon" class="h-5 w-5" />
          </a>
        </div>
      </div>
    </div>

    <div class="container-wide pb-6">
      <div class="border-t border-border pt-6 mt-8 text-center text-xs text-muted-foreground">
        © {{ new Date().getFullYear() }} Psyche Safe. All rights reserved.
      </div>
    </div>
  </footer>
</template>

<script setup>
import { RouterLink } from 'vue-router'
import { Mail, Phone, Linkedin, Twitter, Github } from 'lucide-vue-next'

const footerLinks = [
  { label: 'Home', href: '/' },
  { label: 'About', href: '#about' },
  { label: 'Projects', href: '#projects' },
  { label: 'Skills', href: '#skills' },
  { label: 'Contact', href: '#contact' },
]

const socials = [
  { name: 'GitHub', url: 'https://github.com', icon: Github },
  { name: 'LinkedIn', url: 'https://linkedin.com', icon: Linkedin },
  { name: 'Twitter', url: 'https://twitter.com', icon: Twitter },
]
</script>

<style scoped>
</style>