<template>
  <header
    class="fixed top-0 left-0 right-0 glass border-b backdrop-blur-xl transition-all duration-300"
    :class="{ 'py-3': isScrolled, 'py-5': !isScrolled }"
  >
    <div class="container-wide flex items-center justify-between">
      <!-- Logo -->
      <RouterLink to="/" class="text-2xl font-display font-bold gradient-text">
        Psyche Safe
      </RouterLink>

      <!-- Desktop navigation -->
      <nav class="hidden md:flex items-center gap-8">
        <RouterLink
          v-for="link in navLinks"
          :key="link.href"
          :to="link.href"
          class="relative text-sm font-medium transition-colors hover:text-primary"
          :class="isActive(link.href) ? 'text-primary' : 'text-muted-foreground'"
          @click="closeMobile"
        >
          {{ link.label }}
          <span
            v-if="isActive(link.href)"
            class="absolute -bottom-1 left-0 right-0 h-0.5 bg-primary rounded-full"
          ></span>
        </RouterLink>
      </nav>

      <!-- Controls -->
      <div class="flex items-center gap-4">
        <!-- Theme toggle -->
        <button
          @click="toggleTheme"
          :aria-label="theme === 'dark' ? 'Switch to light mode' : 'Switch to dark mode'"
          class="rounded-lg p-2 text-muted-foreground hover:text-foreground hover:bg-muted transition-all duration-200"
        >
          <Sun class="h-5 w-5" v-show="theme === 'light'" />
          <Moon class="h-5 w-5" v-show="theme === 'dark'" />
        </button>

        <!-- Mobile menu button -->
        <button
          @click="mobileMenuOpen = !mobileMenuOpen"
          :aria-label="mobileMenuOpen ? 'Close menu' : 'Open menu'"
          class="md:hidden rounded-lg p-2 text-muted-foreground hover:text-foreground hover:bg-muted transition-all duration-200"
        >
          <MenuIcon v-show="!mobileMenuOpen" class="h-5 w-5" />
          <X class="h-5 w-5" v-show="mobileMenuOpen" />
        </button>
      </div>
    </div>

    <!-- Mobile navigation -->
    <nav
      v-show="mobileMenuOpen"
      class="md:hidden absolute top-full left-0 right-0 glass border-t backdrop-blur-xl"
    >
      <div class="container-wide py-4 flex flex-col gap-3">
        <RouterLink
          v-for="link in navLinks"
          :key="link.href"
          :to="link.href"
          class="block py-2 text-sm font-medium transition-colors hover:text-primary"
          :class="isActive(link.href) ? 'text-primary' : 'text-muted-foreground'"
          @click="closeMobile"
        >
          {{ link.label }}
        </RouterLink>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'
import { RouterLink, useRoute } from 'vue-router'
import { Sun, Moon, Menu as MenuIcon, X } from 'lucide-vue-next'

const route = useRoute()
const isScrolled = ref(false)
const mobileMenuOpen = ref(false)
const theme = ref('light')

const navLinks = [
  { label: 'Home', href: '/' },
  { label: 'Projects', href: '/#projects' },
  { label: 'Skills', href: '/#skills' },
  { label: 'About', href: '/#about' },
  { label: 'Contact', href: '/#contact' },
]

const scrollY = ref(0)

const handleScroll = () => {
  scrollY.value = window.scrollY
  isScrolled.value = window.scrollY > 50
}

const toggleTheme = () => {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
  document.documentElement.setAttribute('data-theme', theme.value)
  localStorage.setItem('theme', theme.value)
}

const loadTheme = () => {
  const saved = localStorage.getItem('theme')
  if (saved) {
    theme.value = saved
    document.documentElement.setAttribute('data-theme', saved)
  } else {
    document.documentElement.setAttribute('data-theme', 'light')
  }
}

const isActive = (href) => {
  if (href.includes('#')) {
    const section = href.split('#')[1]
    return route.hash === `#${section}`
  }
  return route.path === href
}

const closeMobile = () => {
  mobileMenuOpen.value = false
}

onMounted(() => {
  loadTheme()
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
  position: absolute;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>