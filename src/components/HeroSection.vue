<script setup>
import { ref, onMounted } from 'vue'

const isVisible = ref(false)
const typedText = ref('')
const fullRoles = ['Backend Developer', 'Security Enthusiast', 'EdTech Builder', 'System Architect']
const currentRoleIndex = ref(0)
const isTyping = ref(true)

function typeEffect() {
  const role = fullRoles[currentRoleIndex.value]
  let charIndex = 0
  isTyping.value = true
  typedText.value = ''

  const typeInterval = setInterval(() => {
    if (charIndex < role.length) {
      typedText.value += role[charIndex]
      charIndex++
    } else {
      clearInterval(typeInterval)
      isTyping.value = false
      setTimeout(() => {
        // Erase
        const eraseInterval = setInterval(() => {
          if (typedText.value.length > 0) {
            typedText.value = typedText.value.slice(0, -1)
          } else {
            clearInterval(eraseInterval)
            currentRoleIndex.value = (currentRoleIndex.value + 1) % fullRoles.length
            setTimeout(() => typeEffect(), 300)
          }
        }, 40)
      }, 2200)
    }
  }, 70)
}

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 100)
  setTimeout(() => typeEffect(), 800)
})

const stats = [
  { value: '10+', label: 'Projects', icon: 'fa-solid fa-folder-open', color: 'terracotta' },
  { value: '5+', label: 'Tech Stacks', icon: 'fa-solid fa-layer-group', color: 'sage' },
  { value: '2+', label: 'Years Learning', icon: 'fa-solid fa-graduation-cap', color: 'mustard' },
]
</script>

<template>
  <section id="hero" class="min-h-screen flex items-center relative overflow-hidden pt-20">
    <!-- Decorative background shapes -->
    <div class="absolute top-20 right-10 w-32 h-32 md:w-56 md:h-56 bg-terracotta/8 border-3 border-terracotta/20 rounded-2xl rotate-12 animate-float hidden sm:block"></div>
    <div class="absolute bottom-24 left-5 w-20 h-20 md:w-40 md:h-40 bg-sage/8 border-3 border-sage/20 rounded-2xl -rotate-6 animate-float hidden sm:block" style="animation-delay: 2s"></div>
    <div class="absolute top-1/4 right-1/3 w-16 h-16 bg-mustard/8 border-3 border-mustard/20 rounded-xl rotate-45 animate-float hidden lg:block" style="animation-delay: 4s"></div>

    <!-- Decorative dots -->
    <div class="absolute top-1/3 left-1/4 w-3 h-3 bg-mustard rounded-full animate-pulse-soft hidden md:block"></div>
    <div class="absolute bottom-1/3 right-1/4 w-2 h-2 bg-terracotta rounded-full animate-pulse-soft hidden md:block" style="animation-delay: 1s"></div>
    <div class="absolute top-2/3 left-1/3 w-2 h-2 bg-sage rounded-full animate-pulse-soft hidden md:block" style="animation-delay: 2s"></div>
    <div class="absolute top-1/2 right-1/5 w-3 h-3 bg-lavender rounded-full animate-pulse-soft hidden lg:block" style="animation-delay: 3s"></div>

    <div class="w-full max-w-6xl mx-auto px-5 sm:px-8 py-16 md:py-24">
      <div class="flex flex-col lg:flex-row items-start lg:items-center gap-10 lg:gap-16">
        <!-- Left: Text content -->
        <div class="flex-1 text-left">
          <!-- Greeting badge -->
          <div
            :class="['inline-flex items-center gap-2 px-4 py-2 bg-sage/15 border-3 border-sage rounded-lg shadow-brutal-sm mb-6 md:mb-8 transition-all duration-700', isVisible ? 'animate-fade-in-up' : 'opacity-0']"
          >
            <i class="fa-solid fa-hand-sparkles text-sage"></i>
            <span class="font-mono text-sm text-sage font-medium tracking-wide">Hello, World!</span>
          </div>

          <!-- Name -->
          <h1
            :class="['font-heading font-extrabold text-charcoal leading-[0.95] mb-4 md:mb-6 text-5xl sm:text-6xl md:text-7xl lg:text-8xl transition-all duration-700', isVisible ? 'animate-fade-in-up delay-100' : 'opacity-0']"
          >
            I'm <span class="text-terracotta relative">Abdul<span class="absolute -top-2 -right-4 md:-right-6 text-lg md:text-2xl animate-orbit"><i class="fa-solid fa-sparkle text-mustard text-sm"></i></span></span><span class="text-mustard">.</span>
          </h1>

          <!-- Typed role -->
          <div
            :class="['h-10 sm:h-12 mb-5 md:mb-6 transition-all duration-700', isVisible ? 'animate-fade-in-up delay-200' : 'opacity-0']"
          >
            <h2 class="font-heading font-bold text-charcoal-light text-xl sm:text-2xl md:text-3xl leading-snug">
              <span class="text-sage">{{ typedText }}</span>
              <span class="inline-block w-0.5 h-6 sm:h-7 md:h-8 bg-sage ml-1 align-middle animate-blink"></span>
            </h2>
          </div>

          <!-- Description -->
          <p
            :class="['font-body text-charcoal-muted text-base sm:text-lg max-w-xl leading-relaxed mb-8 md:mb-10 transition-all duration-700', isVisible ? 'animate-fade-in-up delay-300' : 'opacity-0']"
          >
            Crafting robust server architectures, building secure systems, and
            bridging the gap between technology and education. Background in
            <span class="font-semibold text-charcoal">Educational Information Technology</span>.
          </p>

          <!-- CTA Buttons -->
          <div
            :class="['flex flex-wrap gap-3 sm:gap-4 mb-10 lg:mb-0 transition-all duration-700', isVisible ? 'animate-fade-in-up delay-400' : 'opacity-0']"
          >
            <a
              href="#projects"
              class="inline-flex items-center gap-2.5 px-6 sm:px-7 py-3 sm:py-3.5 bg-terracotta text-cream font-heading font-bold text-sm sm:text-base border-3 border-charcoal rounded-lg shadow-brutal hover:shadow-brutal-pressed hover:translate-x-[2px] hover:translate-y-[2px] transition-all duration-150 active:translate-x-[4px] active:translate-y-[4px] active:shadow-none"
            >
              <i class="fa-solid fa-rocket"></i>
              <span>View Projects</span>
            </a>
            <a
              href="#contact"
              class="inline-flex items-center gap-2.5 px-6 sm:px-7 py-3 sm:py-3.5 bg-cream text-charcoal font-heading font-bold text-sm sm:text-base border-3 border-charcoal rounded-lg shadow-brutal hover:shadow-brutal-pressed hover:translate-x-[2px] hover:translate-y-[2px] transition-all duration-150 active:translate-x-[4px] active:translate-y-[4px] active:shadow-none"
            >
              <i class="fa-solid fa-paper-plane"></i>
              <span>Get In Touch</span>
            </a>
          </div>

          <!-- Mobile stats -->
          <div
            :class="['flex gap-4 lg:hidden transition-all duration-700', isVisible ? 'animate-fade-in-up delay-500' : 'opacity-0']"
          >
            <div
              v-for="stat in stats"
              :key="stat.label"
              class="flex-1 bg-cream border-3 border-charcoal rounded-lg shadow-brutal-sm p-3 text-center"
            >
              <i :class="[stat.icon, `text-${stat.color}`, 'text-lg mb-1']"></i>
              <p class="font-heading font-extrabold text-charcoal text-lg leading-none">{{ stat.value }}</p>
              <p class="font-mono text-xs text-charcoal-muted mt-0.5">{{ stat.label }}</p>
            </div>
          </div>
        </div>

        <!-- Right: Decorative card stack (desktop only) -->
        <div
          :class="['hidden lg:flex flex-col gap-4 transition-all duration-700', isVisible ? 'animate-fade-in-up delay-500' : 'opacity-0']"
        >
          <!-- Focus card -->
          <div class="bg-cream border-3 border-charcoal rounded-lg shadow-brutal p-5 w-72 card-interactive">
            <div class="flex items-center gap-3 mb-3">
              <div class="w-11 h-11 bg-terracotta/15 border-3 border-terracotta rounded-lg flex items-center justify-center">
                <i class="fa-solid fa-server text-terracotta"></i>
              </div>
              <div>
                <p class="font-mono text-xs text-charcoal-muted">Focus Area</p>
                <p class="font-heading font-bold text-charcoal text-sm">Backend Systems</p>
              </div>
            </div>
            <div class="flex gap-2 mt-2 flex-wrap">
              <span class="px-2.5 py-1 bg-sage/15 border border-sage rounded text-xs font-mono text-sage font-medium">Laravel</span>
              <span class="px-2.5 py-1 bg-terracotta/15 border border-terracotta rounded text-xs font-mono text-terracotta font-medium">Node.js</span>
              <span class="px-2.5 py-1 bg-mustard/15 border border-mustard rounded text-xs font-mono text-mustard font-medium">PostgreSQL</span>
            </div>
          </div>

          <!-- Security card -->
          <div class="bg-cream border-3 border-charcoal rounded-lg shadow-brutal p-5 w-72 ml-8 card-interactive" style="animation-delay: 0.1s">
            <div class="flex items-center gap-3 mb-3">
              <div class="w-11 h-11 bg-sage/15 border-3 border-sage rounded-lg flex items-center justify-center">
                <i class="fa-solid fa-shield-halved text-sage"></i>
              </div>
              <div>
                <p class="font-mono text-xs text-charcoal-muted">Passion</p>
                <p class="font-heading font-bold text-charcoal text-sm">Security & DevOps</p>
              </div>
            </div>
            <div class="flex gap-2 mt-2 flex-wrap">
              <span class="px-2.5 py-1 bg-sage/15 border border-sage rounded text-xs font-mono text-sage font-medium">Linux</span>
              <span class="px-2.5 py-1 bg-terracotta/15 border border-terracotta rounded text-xs font-mono text-terracotta font-medium">Auth</span>
              <span class="px-2.5 py-1 bg-mustard/15 border border-mustard rounded text-xs font-mono text-mustard font-medium">API Sec</span>
            </div>
          </div>

          <!-- EdTech card -->
          <div class="bg-cream border-3 border-charcoal rounded-lg shadow-brutal p-5 w-72 card-interactive" style="animation-delay: 0.2s">
            <div class="flex items-center gap-3 mb-3">
              <div class="w-11 h-11 bg-mustard/15 border-3 border-mustard rounded-lg flex items-center justify-center">
                <i class="fa-solid fa-book-open text-mustard"></i>
              </div>
              <div>
                <p class="font-mono text-xs text-charcoal-muted">Background</p>
                <p class="font-heading font-bold text-charcoal text-sm">Educational IT</p>
              </div>
            </div>
            <div class="flex gap-2 mt-2 flex-wrap">
              <span class="px-2.5 py-1 bg-sage/15 border border-sage rounded text-xs font-mono text-sage font-medium">EdTech</span>
              <span class="px-2.5 py-1 bg-terracotta/15 border border-terracotta rounded text-xs font-mono text-terracotta font-medium">LMS</span>
              <span class="px-2.5 py-1 bg-lavender/15 border border-lavender rounded text-xs font-mono text-lavender font-medium">UI/UX</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
