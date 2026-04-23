<script setup>
import { ref, onMounted } from 'vue'

const skills = [
  {
    category: 'Backend Development',
    icon: 'fa-solid fa-server',
    accent: 'terracotta',
    items: [
      { name: 'Laravel / PHP', level: 85, icon: 'fa-brands fa-laravel' },
      { name: 'Node.js / Express', level: 75, icon: 'fa-brands fa-node-js' },
      { name: 'REST API Design', level: 80, icon: 'fa-solid fa-plug' },
      { name: 'PostgreSQL', level: 78, icon: 'fa-solid fa-database' },
    ],
  },
  {
    category: 'Security & DevOps',
    icon: 'fa-solid fa-shield-halved',
    accent: 'sage',
    items: [
      { name: 'Authentication (JWT)', level: 82, icon: 'fa-solid fa-key' },
      { name: 'Linux Administration', level: 70, icon: 'fa-brands fa-linux' },
      { name: 'Docker', level: 65, icon: 'fa-brands fa-docker' },
      { name: 'API Security', level: 75, icon: 'fa-solid fa-lock' },
    ],
  },
  {
    category: 'Frontend & Tools',
    icon: 'fa-solid fa-palette',
    accent: 'mustard',
    items: [
      { name: 'Vue 3 / Composition API', level: 80, icon: 'fa-brands fa-vuejs' },
      { name: 'Tailwind CSS', level: 85, icon: 'fa-solid fa-paintbrush' },
      { name: 'Git & Version Control', level: 78, icon: 'fa-brands fa-git-alt' },
      { name: 'Figma / UI Design', level: 60, icon: 'fa-brands fa-figma' },
    ],
  },
]

const animatedLevels = ref({})

onMounted(() => {
  // Initialize all to 0
  skills.forEach((cat) => {
    cat.items.forEach((item) => {
      animatedLevels.value[item.name] = 0
    })
  })

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          // Animate fill after a small delay
          setTimeout(() => {
            skills.forEach((cat) => {
              cat.items.forEach((item) => {
                animatedLevels.value[item.name] = item.level
              })
            })
          }, 300)
          observer.disconnect()
        }
      })
    },
    { threshold: 0.2 }
  )

  const el = document.getElementById('skills')
  if (el) observer.observe(el)
})
</script>

<template>
  <section id="skills" class="py-16 md:py-24 px-5 sm:px-8">
    <div class="max-w-6xl mx-auto">
      <!-- Section header -->
      <div data-aos="fade-up">
        <div class="inline-flex items-center gap-2 px-4 py-2 bg-lavender/15 border-3 border-lavender rounded-lg shadow-brutal-sm mb-5">
          <i class="fa-solid fa-code text-lavender"></i>
          <span class="font-mono text-sm text-lavender font-medium tracking-wide">Tech Arsenal</span>
        </div>
        <h2 class="font-heading font-extrabold text-charcoal text-3xl sm:text-4xl md:text-5xl leading-tight">
          Skills & <span class="text-lavender">Expertise</span>
        </h2>
        <p class="font-body text-charcoal-muted text-base sm:text-lg mt-3 max-w-2xl mb-10 md:mb-14">
          Technologies and tools I work with to build reliable, secure systems.
        </p>
      </div>

      <!-- Skills grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 md:gap-8">
        <div
          v-for="(category, catIndex) in skills"
          :key="category.category"
          data-aos="fade-up"
          :data-aos-delay="catIndex * 120"
          :class="[
            'bg-cream border-3 border-charcoal rounded-xl shadow-brutal p-6 card-interactive',
          ]"
        >
          <!-- Category header -->
          <div class="flex items-center gap-3 mb-6">
            <div
              :class="[
                'w-11 h-11 border-3 rounded-lg flex items-center justify-center',
                `bg-${category.accent}/15 border-${category.accent} text-${category.accent}`,
              ]"
            >
              <i :class="category.icon"></i>
            </div>
            <h3 class="font-heading font-bold text-charcoal text-lg">{{ category.category }}</h3>
          </div>

          <!-- Skill items -->
          <div class="space-y-5">
            <div v-for="item in category.items" :key="item.name">
              <div class="flex items-center justify-between mb-1.5">
                <div class="flex items-center gap-2">
                  <i :class="[item.icon, 'text-sm text-charcoal-muted']"></i>
                  <span class="font-body text-sm font-medium text-charcoal">{{ item.name }}</span>
                </div>
                <span class="font-mono text-xs text-charcoal-faint font-medium">{{ animatedLevels[item.name] || 0 }}%</span>
              </div>
              <!-- Progress bar -->
              <div class="w-full h-3 bg-charcoal/8 rounded-full border border-charcoal/15 overflow-hidden">
                <div
                  class="h-full rounded-full skill-progress-bar relative overflow-hidden"
                  :class="[
                    category.accent === 'terracotta' ? 'bg-terracotta' : category.accent === 'sage' ? 'bg-sage' : 'bg-mustard'
                  ]"
                  :style="{ width: `${animatedLevels[item.name] || 0}%` }"
                >
                  <!-- Shimmer on the progress bar -->
                  <div class="absolute inset-0 animate-shimmer" style="background: linear-gradient(90deg, transparent 0%, rgba(255,255,255,0.25) 50%, transparent 100%); background-size: 200% 100%;"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
