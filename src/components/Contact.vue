<template>
  <section id="contact" class="section bg-muted">
    <div class="container-tight">
      <h2 class="text-4xl font-display font-bold text-center mb-4">
        Get In <span class="text-primary">Touch</span>
      </h2>
      <p class="text-center text-muted-foreground mb-12 max-w-xl mx-auto">
        Have a project in mind or want to collaborate? I'd love to hear from you. Drop me a message and let's create something amazing together.
      </p>

      <div class="grid lg:grid-cols-2 gap-12">
        <!-- Contact Info -->
        <div class="space-y-8">
          <div class="flex items-start gap-4">
            <div class="p-3 rounded-lg bg-primary/10 text-primary">
              <Mail class="h-6 w-6" />
            </div>
            <div>
              <h3 class="font-semibold text-foreground mb-1">Email</h3>
              <a href="mailto:safepsyche@gmail.com" class="text-muted-foreground hover:text-primary transition-colors">
                safepsyche@gmail.com
              </a>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="p-3 rounded-lg bg-primary/10 text-primary">
              <Phone class="h-6 w-6" />
            </div>
            <div>
              <h3 class="font-semibold text-foreground mb-1">Phone</h3>
              <a href="tel:+639175490598" class="text-muted-foreground hover:text-primary transition-colors">
                +63 (917) 549-0598
              </a>
            </div>
          </div>

          <div class="flex items-start gap-4">
            <div class="p-3 rounded-lg bg-primary/10 text-primary">
              <MapPin class="h-6 w-6" />
            </div>
            <div>
              <h3 class="font-semibold text-foreground mb-1">Location</h3>
              <p class="text-muted-foreground">Biñan, Laguna</p>
            </div>
          </div>

          <div class="flex items-center gap-4 pt-4">
            <a
              v-for="social in socials"
              :key="social.name"
              :href="social.url"
              target="_blank"
              rel="noopener noreferrer"
              :aria-label="social.name"
              class="p-3 rounded-lg border border-border text-muted-foreground hover:text-foreground hover:border-primary hover:bg-primary/5 transition-all duration-200"
            >
              <component :is="social.icon" class="h-5 w-5" />
            </a>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="bg-card border border-border rounded-xl p-8 shadow-lg">
          <form @submit.prevent="handleSubmit" class="space-y-6">
            <div class="grid sm:grid-cols-2 gap-6">
              <div>
                <label for="name" class="block text-sm font-medium text-foreground mb-2">Name</label>
                <input
                  id="name"
                  v-model="form.name"
                  type="text"
                  required
                  placeholder="John Doe"
                  class="w-full px-4 py-3 rounded-lg bg-background border border-border text-foreground placeholder:text-muted-foreground focus:outline-none focus:ring-2 focus:ring-primary/50 focus:border-primary transition-all duration-200"
                />
              </div>
              <div>
                <label for="email" class="block text-sm font-medium text-foreground mb-2">Email</label>
                <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  required
                  placeholder="john@example.com"
                  class="w-full px-4 py-3 rounded-lg bg-background border border-border text-foreground placeholder:text-muted-foreground focus:outline-none focus:ring-2 focus:ring-primary/50 focus:border-primary transition-all duration-200"
                />
              </div>
            </div>

            <div>
              <label for="subject" class="block text-sm font-medium text-foreground mb-2">Subject</label>
              <input
                id="subject"
                v-model="form.subject"
                type="text"
                required
                placeholder="Project Inquiry"
                class="w-full px-4 py-3 rounded-lg bg-background border border-border text-foreground placeholder:text-muted-foreground focus:outline-none focus:ring-2 focus:ring-primary/50 focus:border-primary transition-all duration-200"
              />
            </div>

            <div>
              <label for="message" class="block text-sm font-medium text-foreground mb-2">Message</label>
              <textarea
                id="message"
                v-model="form.message"
                rows="5"
                required
                placeholder="Tell me about your project..."
                class="w-full px-4 py-3 rounded-lg bg-background border border-border text-foreground placeholder:text-muted-foreground focus:outline-none focus:ring-2 focus:ring-primary/50 focus:border-primary transition-all duration-200 resize-none"
              ></textarea>
            </div>

            <button
              type="submit"
              :disabled="isSubmitting"
              class="w-full btn btn-primary py-3 text-base disabled:opacity-50 disabled:cursor-not-allowed"
            >
              <span v-if="isSubmitting">Sending...</span>
              <span v-else>Send Message</span>
              <Send class="h-4 w-4" v-if="!isSubmitting" />
            </button>

            <p v-if="submitStatus" class="text-sm text-center" :class="submitStatus.type === 'success' ? 'text-green-500' : 'text-red-500'">
              {{ submitStatus.message }}
            </p>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'
import emailjs from '@emailjs/browser'
import { Mail, Phone, MapPin, Github, Linkedin, Twitter, Send } from 'lucide-vue-next'

const socials = [
  { name: 'GitHub', url: 'https://github.com', icon: Github },
  { name: 'LinkedIn', url: 'https://linkedin.com', icon: Linkedin },
  { name: 'Twitter', url: 'https://twitter.com', icon: Twitter },
]

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: '',
})

const isSubmitting = ref(false)
const submitStatus = ref(null)

// Read EmailJS credentials from environment variables
const SERVICE_ID = import.meta.env.VITE_EMAILJS_SERVICE_ID
const TEMPLATE_ID = import.meta.env.VITE_EMAILJS_TEMPLATE_ID
const CONTACT_TEMPLATE_ID = import.meta.env.VITE_EMAILJS_CONTACT_TEMPLATE_ID
const PUBLIC_KEY = import.meta.env.VITE_EMAILJS_PUBLIC_KEY

const isConfigured = Boolean(
  SERVICE_ID && TEMPLATE_ID && CONTACT_TEMPLATE_ID && PUBLIC_KEY &&
  !SERVICE_ID.includes('your_') &&
  !TEMPLATE_ID.includes('your_') &&
  !CONTACT_TEMPLATE_ID.includes('your_')
)

const handleSubmit = async () => {
  isSubmitting.value = true
  submitStatus.value = null

  if (!isConfigured) {
    // Credentials not set yet — show a helpful message instead of failing silently
    isSubmitting.value = false
    submitStatus.value = {
      type: 'error',
      message: 'Form not configured. Add your EmailJS credentials to .env (see README).',
    }
    return
  }

  // Common payload — variable names match the most common EmailJS template conventions.
  // Both templates use the same field names so we build it once and reuse it.
  const basePayload = {
    from_name: form.name,
    from_email: form.email,
    subject: form.subject,
    message: form.message,
    // Common alternative variable names — match these to your template fields
    name: form.name,
    email: form.email,
    title: form.subject,
  }

  // 1) Auto-reply template — sends the visitor a "thanks, we'll be in touch" message.
  //    Uses {{to_email}} in the template's "To Email" field so it goes to the visitor.
  const autoReplyPayload = {
    ...basePayload,
    to_email: form.email,
  }

  // 2) Contact-us template — sends the inquiry to you.
  //    Template's "To Email" field should be safepsyche@gmail.com.
  const inquiryPayload = {
    ...basePayload,
    to_email: 'safepsyche@gmail.com',
  }

  try {
    // Send both in parallel so the visitor doesn't wait twice as long.
    // If either fails, Promise.all rejects and we surface the error.
    await Promise.all([
      emailjs.send(SERVICE_ID, TEMPLATE_ID, autoReplyPayload, { publicKey: PUBLIC_KEY }),
      emailjs.send(SERVICE_ID, CONTACT_TEMPLATE_ID, inquiryPayload, { publicKey: PUBLIC_KEY }),
    ])

    submitStatus.value = {
      type: 'success',
      message: "Thanks for reaching out! I'll get back to you soon.",
    }

    // Reset form
    form.name = ''
    form.email = ''
    form.subject = ''
    form.message = ''
  } catch (error) {
    console.error('EmailJS error:', error)
    submitStatus.value = {
      type: 'error',
      message: 'Something went wrong. Please try emailing me directly.',
    }
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
</style>