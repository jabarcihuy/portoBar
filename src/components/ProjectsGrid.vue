<script setup>
import Swal from 'sweetalert2'

const projects = [
  {
    id: 'jebolptn',
    name: 'JebolPTN',
    tagline: 'UTBK Tryout Platform',
    description:
      'A full-stack exam simulation platform for Indonesian university entrance preparation. Features real-time scoring, analytics dashboards, and thousands of curated questions across TPS & TKA categories.',
    tags: ['Laravel', 'PostgreSQL', 'REST API', 'Redis', 'Vue.js'],
    accent: 'terracotta',
    icon: 'fa-solid fa-bullseye',
    stats: [
      { label: 'Questions', value: '5000+', icon: 'fa-solid fa-circle-question' },
      { label: 'Users', value: '1.2K+', icon: 'fa-solid fa-users' },
    ],
    features: ['Real-time Scoring', 'Analytics Dashboard', 'Question Bank Management'],
    featureIcons: ['fa-solid fa-bolt', 'fa-solid fa-chart-line', 'fa-solid fa-database'],
    longDescription: `<div style="text-align: left; font-family: 'Inter', sans-serif;">
      <p style="margin-bottom: 12px; color: #5D6D7E;">JebolPTN is a comprehensive UTBK (Ujian Tulis Berbasis Komputer) simulation platform designed to help Indonesian high school students prepare for university entrance exams.</p>
      <h4 style="font-family: 'Plus Jakarta Sans', sans-serif; color: #2C3E50; margin-bottom: 8px;">🎯 Key Features</h4>
      <ul style="color: #5D6D7E; padding-left: 20px; margin-bottom: 12px;">
        <li>5000+ curated questions across TPS & TKA</li>
        <li>Real-time scoring with detailed analytics</li>
        <li>Performance tracking over time</li>
        <li>Redis-cached session management</li>
      </ul>
      <h4 style="font-family: 'Plus Jakarta Sans', sans-serif; color: #2C3E50; margin-bottom: 8px;">⚙️ Tech Stack</h4>
      <p style="color: #5D6D7E;">Laravel 10, PostgreSQL, Redis, Vue.js, REST API, JWT Authentication</p>
    </div>`,
  },
  {
    id: 'kelaskita',
    name: 'KelasKita',
    tagline: 'Academic Scheduling & Task Management',
    description:
      'Unified class management platform for university students. Handles scheduling, assignments, grade tracking, and collaborative study tools within an intuitive interface.',
    tags: ['Vue 3', 'Express.js', 'PostgreSQL', 'Tailwind CSS', 'JWT Auth'],
    accent: 'sage',
    icon: 'fa-solid fa-graduation-cap',
    stats: [
      { label: 'Modules', value: '12+', icon: 'fa-solid fa-puzzle-piece' },
      { label: 'Active Classes', value: '50+', icon: 'fa-solid fa-chalkboard' },
    ],
    features: ['Smart Scheduling', 'Task Tracker', 'Grade Analytics'],
    featureIcons: ['fa-solid fa-calendar-check', 'fa-solid fa-list-check', 'fa-solid fa-chart-pie'],
    longDescription: `<div style="text-align: left; font-family: 'Inter', sans-serif;">
      <p style="margin-bottom: 12px; color: #5D6D7E;">KelasKita is an all-in-one academic management platform designed for Indonesian university students to streamline their daily academic workflow.</p>
      <h4 style="font-family: 'Plus Jakarta Sans', sans-serif; color: #2C3E50; margin-bottom: 8px;">📚 Key Features</h4>
      <ul style="color: #5D6D7E; padding-left: 20px; margin-bottom: 12px;">
        <li>Automatic schedule conflict detection</li>
        <li>Assignment deadline tracker with reminders</li>
        <li>Grade analytics with GPA projection</li>
        <li>Collaborative study group tools</li>
      </ul>
      <h4 style="font-family: 'Plus Jakarta Sans', sans-serif; color: #2C3E50; margin-bottom: 8px;">⚙️ Tech Stack</h4>
      <p style="color: #5D6D7E;">Vue 3, Express.js, PostgreSQL, Tailwind CSS, JWT + Refresh Tokens</p>
    </div>`,
  },
]

function showProjectDetail(project) {
  Swal.fire({
    title: `${project.name}`,
    html: project.longDescription,
    width: 600,
    confirmButtonText: '<i class="fa-solid fa-arrow-right"></i> Awesome!',
    confirmButtonColor: project.accent === 'terracotta' ? '#C0755A' : '#7D9B76',
    showClass: {
      popup: 'animate__animated animate__fadeInUp animate__faster',
    },
    hideClass: {
      popup: 'animate__animated animate__fadeOutDown animate__faster',
    },
  })
}
</script>

<template>
  <section id="projects" class="py-16 md:py-24 px-5 sm:px-8">
    <div class="max-w-6xl mx-auto">
      <!-- Section header -->
      <div data-aos="fade-up">
        <div class="inline-flex items-center gap-2 px-4 py-2 bg-terracotta/15 border-3 border-terracotta rounded-lg shadow-brutal-sm mb-5">
          <i class="fa-solid fa-rocket text-terracotta"></i>
          <span class="font-mono text-sm text-terracotta font-medium tracking-wide">Featured Projects</span>
        </div>
        <h2 class="font-heading font-extrabold text-charcoal text-3xl sm:text-4xl md:text-5xl leading-tight">
          Things I've <span class="text-terracotta">Built</span>
        </h2>
        <p class="font-body text-charcoal-muted text-base sm:text-lg mt-3 max-w-2xl mb-10 md:mb-14">
          Full-stack web platforms designed to solve real problems in education and productivity.
        </p>
      </div>

      <!-- Bento Grid -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 md:gap-8">
        <div
          v-for="(project, index) in projects"
          :key="project.id"
          :data-aos="index % 2 === 0 ? 'fade-right' : 'fade-left'"
          :data-aos-delay="index * 100"
          :class="[
            'group bg-cream border-3 rounded-xl p-6 sm:p-8 transition-all duration-200 cursor-pointer relative overflow-hidden',
            project.accent === 'terracotta'
              ? 'border-terracotta shadow-brutal-terracotta hover:translate-x-[2px] hover:translate-y-[2px] hover:shadow-[3px_3px_0px_var(--color-terracotta)]'
              : 'border-sage shadow-brutal-sage hover:translate-x-[2px] hover:translate-y-[2px] hover:shadow-[3px_3px_0px_var(--color-sage)]',
          ]"
          @click="showProjectDetail(project)"
        >
          <!-- Shimmer effect on hover -->
          <div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 animate-shimmer pointer-events-none rounded-xl"></div>

          <!-- Header -->
          <div class="flex flex-col sm:flex-row sm:items-start justify-between gap-4 mb-5 relative">
            <div class="flex items-center gap-3">
              <div
                :class="[
                  'w-13 h-13 sm:w-14 sm:h-14 border-3 rounded-xl flex items-center justify-center text-xl shrink-0 transition-transform duration-300 group-hover:scale-110 group-hover:rotate-3',
                  project.accent === 'terracotta' ? 'bg-terracotta/10 border-terracotta text-terracotta' : 'bg-sage/10 border-sage text-sage',
                ]"
              >
                <i :class="project.icon"></i>
              </div>
              <div>
                <h3 class="font-heading font-extrabold text-charcoal text-xl sm:text-2xl flex items-center gap-2">
                  {{ project.name }}
                  <i class="fa-solid fa-arrow-up-right-from-square text-xs text-charcoal-faint group-hover:text-charcoal-muted transition-colors"></i>
                </h3>
                <p
                  :class="[
                    'font-mono text-xs sm:text-sm font-medium',
                    project.accent === 'terracotta' ? 'text-terracotta' : 'text-sage',
                  ]"
                >
                  {{ project.tagline }}
                </p>
              </div>
            </div>

            <!-- Stats -->
            <div class="flex gap-3 sm:gap-4">
              <div
                v-for="stat in project.stats"
                :key="stat.label"
                class="text-center"
              >
                <div class="flex items-center justify-center gap-1 mb-0.5">
                  <i :class="[stat.icon, 'text-xs text-charcoal-faint']"></i>
                  <p class="font-heading font-extrabold text-charcoal text-lg sm:text-xl leading-none">{{ stat.value }}</p>
                </div>
                <p class="font-mono text-xs text-charcoal-muted">{{ stat.label }}</p>
              </div>
            </div>
          </div>

          <!-- Description -->
          <p class="font-body text-charcoal-muted text-sm sm:text-base leading-relaxed mb-5 relative">
            {{ project.description }}
          </p>

          <!-- Features -->
          <div class="flex flex-wrap gap-2 mb-5">
            <div
              v-for="(feature, fi) in project.features"
              :key="feature"
              :class="[
                'flex items-center gap-1.5 px-3 py-1.5 rounded-lg border text-xs sm:text-sm font-body font-medium transition-all duration-200 hover:scale-105',
                project.accent === 'terracotta'
                  ? 'bg-terracotta/8 border-terracotta/30 text-terracotta'
                  : 'bg-sage/8 border-sage/30 text-sage',
              ]"
            >
              <i :class="[project.featureIcons[fi], 'text-xs']"></i>
              {{ feature }}
            </div>
          </div>

          <!-- Tech tags -->
          <div class="flex flex-wrap gap-2 relative">
            <span
              v-for="tag in project.tags"
              :key="tag"
              class="px-2.5 py-1 bg-charcoal/5 border border-charcoal/20 rounded text-xs font-mono text-charcoal-light font-medium hover:bg-charcoal/10 transition-colors duration-200"
            >
              {{ tag }}
            </span>
          </div>

          <!-- Click hint -->
          <div class="mt-4 pt-4 border-t border-charcoal/10 flex items-center gap-2 text-xs font-mono text-charcoal-faint group-hover:text-charcoal-muted transition-colors">
            <i class="fa-solid fa-hand-pointer"></i>
            <span>Click for details</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
