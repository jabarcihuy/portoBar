<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import ProjectsGrid from './components/ProjectsGrid.vue'
import SkillsSection from './components/SkillsSection.vue'
import HardwareSection from './components/HardwareSection.vue'
import TerminalWindow from './components/TerminalWindow.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'

const showBackToTop = ref(false)

function handleScroll() {
  showBackToTop.value = window.scrollY > 600
}

function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <div class="min-h-screen bg-cream">
    <!-- ═══ Navigation ═══ -->
    <NavBar />

    <!-- ═══ Hero ═══ -->
    <HeroSection />

    <!-- ═══ Section Divider ═══ -->
    <div class="max-w-6xl mx-auto px-5 sm:px-8">
      <div class="border-t-3 border-charcoal/12 relative">
        <div class="absolute left-1/2 -translate-x-1/2 -top-3 bg-cream px-4">
          <div class="w-6 h-6 border-3 border-charcoal/25 rounded-full bg-cream flex items-center justify-center">
            <div class="w-2 h-2 bg-terracotta rounded-full"></div>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ Featured Projects ═══ -->
    <ProjectsGrid />

    <!-- ═══ Section Divider ═══ -->
    <div class="max-w-6xl mx-auto px-5 sm:px-8">
      <div class="border-t-3 border-charcoal/12 relative">
        <div class="absolute left-1/2 -translate-x-1/2 -top-3 bg-cream px-4">
          <div class="w-6 h-6 border-3 border-charcoal/25 rounded-full bg-cream flex items-center justify-center">
            <div class="w-2 h-2 bg-lavender rounded-full"></div>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ Skills & Expertise ═══ -->
    <SkillsSection />

    <!-- ═══ Section Divider ═══ -->
    <div class="max-w-6xl mx-auto px-5 sm:px-8">
      <div class="border-t-3 border-charcoal/12 relative">
        <div class="absolute left-1/2 -translate-x-1/2 -top-3 bg-cream px-4">
          <div class="w-6 h-6 border-3 border-charcoal/25 rounded-full bg-cream flex items-center justify-center">
            <div class="w-2 h-2 bg-mustard rounded-full"></div>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ Hardware & Embedded ═══ -->
    <HardwareSection />

    <!-- ═══ Section Divider ═══ -->
    <div class="max-w-6xl mx-auto px-5 sm:px-8">
      <div class="border-t-3 border-charcoal/12 relative">
        <div class="absolute left-1/2 -translate-x-1/2 -top-3 bg-cream-dark px-4">
          <div class="w-6 h-6 border-3 border-charcoal/25 rounded-full bg-cream-dark flex items-center justify-center">
            <div class="w-2 h-2 bg-sage rounded-full"></div>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ Terminal Showcase ═══ -->
    <TerminalWindow />

    <!-- ═══ Section Divider ═══ -->
    <div class="max-w-6xl mx-auto px-5 sm:px-8">
      <div class="border-t-3 border-charcoal/12 relative">
        <div class="absolute left-1/2 -translate-x-1/2 -top-3 bg-cream px-4">
          <div class="w-6 h-6 border-3 border-charcoal/25 rounded-full bg-cream flex items-center justify-center">
            <div class="w-2 h-2 bg-rose rounded-full"></div>
          </div>
        </div>
      </div>
    </div>

    <!-- ═══ Contact ═══ -->
    <ContactSection />

    <!-- ═══ Footer ═══ -->
    <FooterSection />

    <!-- ═══ Back to Top ═══ -->
    <transition
      enter-active-class="transition-all duration-300 ease-out"
      enter-from-class="opacity-0 translate-y-4 scale-90"
      enter-to-class="opacity-100 translate-y-0 scale-100"
      leave-active-class="transition-all duration-200 ease-in"
      leave-from-class="opacity-100 translate-y-0 scale-100"
      leave-to-class="opacity-0 translate-y-4 scale-90"
    >
      <button
        v-if="showBackToTop"
        @click="scrollToTop"
        class="fixed bottom-6 right-6 z-40 w-12 h-12 bg-terracotta text-cream border-3 border-charcoal rounded-xl shadow-brutal flex items-center justify-center hover:shadow-brutal-pressed hover:translate-x-[2px] hover:translate-y-[2px] transition-all duration-150 active:translate-x-[4px] active:translate-y-[4px] active:shadow-none"
        aria-label="Back to top"
      >
        <i class="fa-solid fa-arrow-up text-sm"></i>
      </button>
    </transition>
  </div>
</template>
