<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)
const activeSection = ref('hero')

const navLinks = [
  { id: 'hero', label: 'Home', icon: 'fa-solid fa-house' },
  { id: 'projects', label: 'Projects', icon: 'fa-solid fa-rocket' },
  { id: 'skills', label: 'Skills', icon: 'fa-solid fa-code' },
  { id: 'hardware', label: 'Hardware', icon: 'fa-solid fa-microchip' },
  { id: 'terminal', label: 'Terminal', icon: 'fa-solid fa-terminal' },
  { id: 'contact', label: 'Contact', icon: 'fa-solid fa-envelope' },
]

function handleScroll() {
  isScrolled.value = window.scrollY > 50

  // Scroll spy
  const sections = navLinks.map((l) => document.getElementById(l.id)).filter(Boolean)
  const scrollPos = window.scrollY + 120

  for (let i = sections.length - 1; i >= 0; i--) {
    if (sections[i].offsetTop <= scrollPos) {
      activeSection.value = sections[i].id
      break
    }
  }
}

function scrollTo(id) {
  isMobileMenuOpen.value = false
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' })
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      isScrolled
        ? 'nav-glass bg-cream/85 border-b-3 border-charcoal/20 shadow-[0_4px_20px_rgba(44,62,80,0.08)]'
        : 'bg-transparent',
    ]"
  >
    <div class="max-w-6xl mx-auto px-5 sm:px-8">
      <div class="flex items-center justify-between h-16 md:h-18">
        <!-- Logo -->
        <button
          @click="scrollTo('hero')"
          class="font-heading font-extrabold text-xl md:text-2xl text-charcoal hover:text-terracotta transition-colors duration-200 flex items-center gap-2"
        >
          <span class="w-8 h-8 md:w-9 md:h-9 bg-terracotta text-cream rounded-lg border-2 border-charcoal flex items-center justify-center text-sm font-extrabold shadow-[2px_2px_0px_var(--color-charcoal)]">A</span>
          <span class="hidden sm:inline">Abdul<span class="text-terracotta">.</span></span>
        </button>

        <!-- Desktop nav links -->
        <div class="hidden md:flex items-center gap-1">
          <button
            v-for="link in navLinks"
            :key="link.id"
            @click="scrollTo(link.id)"
            :class="[
              'px-3 lg:px-4 py-2 rounded-lg font-body text-sm font-medium transition-all duration-200 flex items-center gap-2',
              activeSection === link.id
                ? 'bg-charcoal text-cream shadow-[2px_2px_0px_var(--color-terracotta)]'
                : 'text-charcoal-muted hover:text-charcoal hover:bg-charcoal/5',
            ]"
          >
            <i :class="[link.icon, 'text-xs']"></i>
            <span>{{ link.label }}</span>
          </button>
        </div>

        <!-- Mobile menu toggle -->
        <button
          @click="isMobileMenuOpen = !isMobileMenuOpen"
          class="md:hidden w-10 h-10 bg-cream border-2 border-charcoal rounded-lg flex items-center justify-center shadow-[2px_2px_0px_var(--color-charcoal)] hover:translate-x-[1px] hover:translate-y-[1px] hover:shadow-[1px_1px_0px_var(--color-charcoal)] transition-all duration-150"
          aria-label="Toggle menu"
        >
          <i :class="isMobileMenuOpen ? 'fa-solid fa-xmark' : 'fa-solid fa-bars'" class="text-charcoal"></i>
        </button>
      </div>
    </div>

    <!-- Mobile dropdown -->
    <transition
      enter-active-class="transition-all duration-300 ease-out"
      enter-from-class="opacity-0 -translate-y-4 scale-95"
      enter-to-class="opacity-100 translate-y-0 scale-100"
      leave-active-class="transition-all duration-200 ease-in"
      leave-from-class="opacity-100 translate-y-0 scale-100"
      leave-to-class="opacity-0 -translate-y-4 scale-95"
    >
      <div
        v-if="isMobileMenuOpen"
        class="md:hidden bg-cream border-b-3 border-charcoal/20 shadow-[0_8px_24px_rgba(44,62,80,0.1)] px-5 pb-4"
      >
        <button
          v-for="link in navLinks"
          :key="link.id"
          @click="scrollTo(link.id)"
          :class="[
            'w-full text-left px-4 py-3 rounded-lg font-body text-sm font-medium transition-all duration-200 flex items-center gap-3 mb-1',
            activeSection === link.id
              ? 'bg-charcoal text-cream shadow-[2px_2px_0px_var(--color-terracotta)]'
              : 'text-charcoal-muted hover:text-charcoal hover:bg-charcoal/5',
          ]"
        >
          <i :class="[link.icon, 'w-4 text-center']"></i>
          <span>{{ link.label }}</span>
        </button>
      </div>
    </transition>
  </nav>
</template>
