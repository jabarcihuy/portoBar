<script setup>
const currentYear = new Date().getFullYear()

const navLinks = [
  { id: 'hero', label: 'Home', icon: 'fa-solid fa-house' },
  { id: 'projects', label: 'Projects', icon: 'fa-solid fa-rocket' },
  { id: 'skills', label: 'Skills', icon: 'fa-solid fa-code' },
  { id: 'hardware', label: 'Hardware', icon: 'fa-solid fa-microchip' },
  { id: 'terminal', label: 'Terminal', icon: 'fa-solid fa-terminal' },
  { id: 'contact', label: 'Contact', icon: 'fa-solid fa-envelope' },
]

const socials = [
  { icon: 'fa-brands fa-github', label: 'GitHub', href: '#' },
  { icon: 'fa-brands fa-linkedin-in', label: 'LinkedIn', href: '#' },
  { icon: 'fa-brands fa-twitter', label: 'Twitter', href: '#' },
  { icon: 'fa-solid fa-envelope', label: 'Email', href: 'mailto:abdul@example.com' },
]

function scrollTo(id) {
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <footer id="footer" class="py-12 md:py-16 px-5 sm:px-8 bg-charcoal relative overflow-hidden">
    <!-- Decorative elements -->
    <div class="absolute top-0 right-0 w-32 h-32 bg-terracotta/5 rounded-bl-[80px]"></div>
    <div class="absolute bottom-0 left-0 w-24 h-24 bg-sage/5 rounded-tr-[60px]"></div>

    <div class="max-w-6xl mx-auto relative">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-10 md:gap-8">
        <!-- Left: Brand -->
        <div>
          <h3 class="font-heading font-extrabold text-cream text-2xl sm:text-3xl mb-3 flex items-center gap-2">
            <span class="w-9 h-9 bg-terracotta text-cream rounded-lg border-2 border-cream/20 flex items-center justify-center text-sm font-extrabold">A</span>
            Abdul<span class="text-terracotta">.</span>
          </h3>
          <p class="font-body text-cream/40 text-sm leading-relaxed max-w-xs mb-5">
            Backend Developer & Security Enthusiast building solutions at the intersection of technology and education.
          </p>
          <!-- Social icons -->
          <div class="flex gap-3">
            <a
              v-for="social in socials"
              :key="social.label"
              :href="social.href"
              :aria-label="social.label"
              class="w-10 h-10 bg-terminal-bg border-2 border-cream/15 rounded-lg flex items-center justify-center hover:border-terracotta hover:bg-terracotta/10 transition-all duration-200 group"
            >
              <i :class="[social.icon, 'text-cream/50 group-hover:text-terracotta transition-colors duration-200']"></i>
            </a>
          </div>
        </div>

        <!-- Center: Quick links -->
        <div>
          <h4 class="font-heading font-bold text-cream/60 text-xs uppercase tracking-[0.2em] mb-4 flex items-center gap-2">
            <i class="fa-solid fa-compass text-cream/30"></i>
            Navigate
          </h4>
          <div class="grid grid-cols-2 gap-2">
            <button
              v-for="link in navLinks"
              :key="link.id"
              @click="scrollTo(link.id)"
              class="flex items-center gap-2 text-left font-body text-cream/40 hover:text-terracotta text-sm transition-all duration-200 py-1.5 group"
            >
              <i :class="[link.icon, 'text-xs w-4 text-cream/25 group-hover:text-terracotta transition-colors']"></i>
              {{ link.label }}
            </button>
          </div>
        </div>

        <!-- Right: Tech badge -->
        <div>
          <h4 class="font-heading font-bold text-cream/60 text-xs uppercase tracking-[0.2em] mb-4 flex items-center gap-2">
            <i class="fa-solid fa-wrench text-cream/30"></i>
            Built With
          </h4>
          <div class="flex flex-wrap gap-2">
            <span
              v-for="tech in ['Vue 3', 'Tailwind CSS', 'Vite', 'SweetAlert2', 'AOS', 'FontAwesome']"
              :key="tech"
              class="px-3 py-1.5 bg-terminal-bg border border-cream/10 rounded-lg font-mono text-xs text-cream/35 hover:border-cream/25 hover:text-cream/50 transition-all duration-200"
            >
              {{ tech }}
            </span>
          </div>

          <!-- Fun status -->
          <div class="mt-5 flex items-center gap-2 font-mono text-xs text-cream/25">
            <div class="relative">
              <div class="w-2 h-2 bg-sage rounded-full"></div>
              <div class="w-2 h-2 bg-sage rounded-full absolute inset-0 animate-ping opacity-40"></div>
            </div>
            <span>Status: Building cool stuff</span>
          </div>
        </div>
      </div>

      <!-- Divider -->
      <div class="border-t border-cream/8 mt-10 pt-6 flex flex-col sm:flex-row items-center justify-between gap-3">
        <p class="font-mono text-xs text-cream/25 flex items-center gap-1.5">
          <i class="fa-regular fa-copyright"></i>
          {{ currentYear }} Abdul. All rights reserved.
        </p>
        <p class="font-mono text-xs text-cream/25 flex items-center gap-1.5">
          Crafted with <i class="fa-solid fa-heart text-terracotta/60 mx-0.5"></i> and
          <i class="fa-solid fa-mug-hot text-mustard/60 mx-0.5"></i>
        </p>
      </div>
    </div>
  </footer>
</template>
