<script setup>
import Swal from 'sweetalert2'

const projects = [
  {
    id: 'jebolptn',
    name: 'JebolPTN',
    tagline: 'UTBK Tryout Platform',
    description:
      'Battle-tested exam simulation engine that arms students with 5000+ strategically curated questions, real-time performance analytics, and Redis-accelerated sessions — turning UTBK preparation from guesswork into a data-driven campaign.',
    tags: ['Laravel', 'PostgreSQL', 'REST API', 'Redis', 'Vue.js'],
    accent: 'terracotta',
    icon: 'fa-solid fa-bullseye',
    stats: [
      { label: 'Questions', value: '5000+', icon: 'fa-solid fa-circle-question' },
      { label: 'Users', value: '1.2K+', icon: 'fa-solid fa-users' },
    ],
    features: ['Real-time Scoring', 'Analytics Dashboard', 'Question Bank Management'],
    featureIcons: ['fa-solid fa-bolt', 'fa-solid fa-chart-line', 'fa-solid fa-database'],
    longDescription: `<div class="text-left font-body">
      <div class="bg-terracotta/15 border-3 border-charcoal rounded-xl p-5 mb-6 shadow-brutal-sm relative overflow-hidden">
        <div class="absolute -right-4 -top-4 opacity-10">
          <i class="fa-solid fa-bullseye text-8xl text-charcoal"></i>
        </div>
        <p class="text-charcoal leading-relaxed text-sm md:text-base relative z-10 font-medium">JebolPTN is a high-performance UTBK simulation platform engineered to transform how Indonesian students prepare for university entrance exams. Every component is purpose-built for speed, accuracy, and actionable insight.</p>
      </div>
      <h4 class="font-heading font-extrabold text-charcoal text-lg mb-4 flex items-center gap-3">
        <div class="w-10 h-10 rounded-lg bg-cream-dark border-3 border-charcoal flex items-center justify-center shadow-brutal-sm">
          <i class="fa-solid fa-crosshairs text-terracotta"></i>
        </div>
        Key Features
      </h4>
      <ul class="space-y-3 mb-6">
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-terracotta hover:bg-terracotta/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-check text-terracotta"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">5000+ expert-curated questions spanning TPS & TKA domains</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-terracotta hover:bg-terracotta/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-bolt text-terracotta"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Instant scoring with granular per-question analytics</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-terracotta hover:bg-terracotta/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-chart-line text-terracotta"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Historical performance tracking with trend visualization</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-terracotta hover:bg-terracotta/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-server text-terracotta"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Redis-cached session management for sub-100ms response times</span>
        </li>
      </ul>
      <h4 class="font-heading font-extrabold text-charcoal text-lg mb-3 flex items-center gap-3">
        <div class="w-10 h-10 rounded-lg bg-cream-dark border-3 border-charcoal flex items-center justify-center shadow-brutal-sm">
          <i class="fa-solid fa-gears text-terracotta"></i>
        </div>
        Tech Stack
      </h4>
      <div class="flex flex-wrap gap-2">
        <span class="px-3 py-1 bg-terracotta/10 border-2 border-terracotta/40 text-terracotta rounded-md text-xs font-mono font-bold">Laravel 10</span>
        <span class="px-3 py-1 bg-terracotta/10 border-2 border-terracotta/40 text-terracotta rounded-md text-xs font-mono font-bold">PostgreSQL</span>
        <span class="px-3 py-1 bg-terracotta/10 border-2 border-terracotta/40 text-terracotta rounded-md text-xs font-mono font-bold">Redis</span>
        <span class="px-3 py-1 bg-terracotta/10 border-2 border-terracotta/40 text-terracotta rounded-md text-xs font-mono font-bold">Vue.js</span>
        <span class="px-3 py-1 bg-terracotta/10 border-2 border-terracotta/40 text-terracotta rounded-md text-xs font-mono font-bold">REST API</span>
      </div>
    </div>`,
  },
  {
    id: 'kelaskita',
    name: 'KelasKita',
    tagline: 'Academic Scheduling & Task Management',
    description:
      'The command center for university life — an integrated platform that weaves together class scheduling, assignment tracking, and grade analytics into a single cohesive workflow, empowering students to own their academic trajectory.',
    tags: ['Vue 3', 'Express.js', 'PostgreSQL', 'Tailwind CSS', 'JWT Auth'],
    accent: 'sage',
    icon: 'fa-solid fa-graduation-cap',
    stats: [
      { label: 'Modules', value: '12+', icon: 'fa-solid fa-puzzle-piece' },
      { label: 'Active Classes', value: '50+', icon: 'fa-solid fa-chalkboard' },
    ],
    features: ['Smart Scheduling', 'Task Tracker', 'Grade Analytics'],
    featureIcons: ['fa-solid fa-calendar-check', 'fa-solid fa-list-check', 'fa-solid fa-chart-pie'],
    longDescription: `<div class="text-left font-body">
      <div class="bg-sage/15 border-3 border-charcoal rounded-xl p-5 mb-6 shadow-brutal-sm relative overflow-hidden">
        <div class="absolute -right-4 -top-4 opacity-10">
          <i class="fa-solid fa-graduation-cap text-8xl text-charcoal"></i>
        </div>
        <p class="text-charcoal leading-relaxed text-sm md:text-base relative z-10 font-medium">KelasKita reimagines how Indonesian university students manage their academic lives — replacing scattered notes and fragmented tools with one unified, intelligent platform built from the ground up for the university workflow.</p>
      </div>
      <h4 class="font-heading font-extrabold text-charcoal text-lg mb-4 flex items-center gap-3">
        <div class="w-10 h-10 rounded-lg bg-cream-dark border-3 border-charcoal flex items-center justify-center shadow-brutal-sm">
          <i class="fa-solid fa-book-open text-sage"></i>
        </div>
        Key Features
      </h4>
      <ul class="space-y-3 mb-6">
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-sage hover:bg-sage/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-calendar-check text-sage"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Intelligent schedule conflict detection that prevents overlaps before they happen</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-sage hover:bg-sage/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-list-check text-sage"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Assignment deadline tracker with configurable push reminders</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-sage hover:bg-sage/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-chart-pie text-sage"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Grade analytics engine with semester GPA projection</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-sage hover:bg-sage/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-users text-sage"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Collaborative study group tools for peer-to-peer learning</span>
        </li>
      </ul>
      <h4 class="font-heading font-extrabold text-charcoal text-lg mb-3 flex items-center gap-3">
        <div class="w-10 h-10 rounded-lg bg-cream-dark border-3 border-charcoal flex items-center justify-center shadow-brutal-sm">
          <i class="fa-solid fa-gears text-sage"></i>
        </div>
        Tech Stack
      </h4>
      <div class="flex flex-wrap gap-2">
        <span class="px-3 py-1 bg-sage/10 border-2 border-sage/40 text-sage rounded-md text-xs font-mono font-bold">Vue 3</span>
        <span class="px-3 py-1 bg-sage/10 border-2 border-sage/40 text-sage rounded-md text-xs font-mono font-bold">Express.js</span>
        <span class="px-3 py-1 bg-sage/10 border-2 border-sage/40 text-sage rounded-md text-xs font-mono font-bold">PostgreSQL</span>
        <span class="px-3 py-1 bg-sage/10 border-2 border-sage/40 text-sage rounded-md text-xs font-mono font-bold">Tailwind CSS</span>
        <span class="px-3 py-1 bg-sage/10 border-2 border-sage/40 text-sage rounded-md text-xs font-mono font-bold">JWT</span>
      </div>
    </div>`,
  },
  {
    id: 'bot-wa',
    name: 'WhatsApp Keyword Bot',
    tagline: 'Auto-Reply & Product Manager Bot',
    description:
      'A lightweight conversational automation layer for WhatsApp — matches incoming messages against configurable keyword rules and fires instant replies, with a built-in admin CLI for managing product catalogs without ever touching the codebase.',
    tags: ['Node.js', 'whatsapp-web.js', 'JSON DB', 'QR Auth'],
    accent: 'mustard',
    icon: 'fa-brands fa-whatsapp',
    stats: [
      { label: 'Setup', value: 'QR Code', icon: 'fa-solid fa-qrcode' },
      { label: 'Config', value: 'JSON', icon: 'fa-solid fa-file-code' },
    ],
    features: ['Keyword Auto-Reply', 'Admin Commands', 'Group Support'],
    featureIcons: ['fa-solid fa-reply-all', 'fa-solid fa-user-shield', 'fa-solid fa-users'],
    longDescription: `<div class="text-left font-body">
      <div class="bg-mustard/15 border-3 border-charcoal rounded-xl p-5 mb-6 shadow-brutal-sm relative overflow-hidden">
        <div class="absolute -right-4 -top-4 opacity-10">
          <i class="fa-brands fa-whatsapp text-8xl text-charcoal"></i>
        </div>
        <p class="text-charcoal leading-relaxed text-sm md:text-base relative z-10 font-medium">A zero-ui automation engine built on <strong class="font-bold border-b-2 border-mustard">whatsapp-web.js</strong> — designed to intercept, parse, and respond to messages using smart keyword matching across private and group conversations simultaneously.</p>
      </div>
      <h4 class="font-heading font-extrabold text-charcoal text-lg mb-4 flex items-center gap-3">
        <div class="w-10 h-10 rounded-lg bg-cream-dark border-3 border-charcoal flex items-center justify-center shadow-brutal-sm">
          <i class="fa-solid fa-rocket text-mustard"></i>
        </div>
        Key Features
      </h4>
      <ul class="space-y-3 mb-6">
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-mustard hover:bg-mustard/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-reply-all text-mustard"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium"><strong class="text-charcoal font-bold">Smart Auto-Reply:</strong> Dynamic response matching from <code class="font-mono text-xs bg-mustard/20 px-1 py-0.5 border border-mustard rounded">responses.json</code> with longest-keyword-first prioritization</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-mustard hover:bg-mustard/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-user-shield text-mustard"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium"><strong class="text-charcoal font-bold">Admin Commands:</strong> Authorized users manage keyword-response pairs directly from WhatsApp — no deployment needed</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-mustard hover:bg-mustard/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-users text-mustard"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium"><strong class="text-charcoal font-bold">Group Chat Support:</strong> Seamlessly monitors and responds inside any WhatsApp group the bot is a member of</span>
        </li>
      </ul>
      <h4 class="font-heading font-extrabold text-charcoal text-lg mb-3 flex items-center gap-3">
        <div class="w-10 h-10 rounded-lg bg-cream-dark border-3 border-charcoal flex items-center justify-center shadow-brutal-sm">
          <i class="fa-solid fa-shield-halved text-mustard"></i>
        </div>
        Admin Capabilities
      </h4>
      <div class="bg-cream p-4 rounded-lg border-2 border-charcoal/20 mb-6">
        <p class="text-charcoal-muted text-sm md:text-base font-medium leading-relaxed">Product CRUD via chat: <code class="font-mono text-xs bg-mustard/20 px-1 py-0.5 border border-mustard rounded">admin addproduk</code>, <code class="font-mono text-xs bg-mustard/20 px-1 py-0.5 border border-mustard rounded">admin hapusproduk</code>, <code class="font-mono text-xs bg-mustard/20 px-1 py-0.5 border border-mustard rounded">admin listproduk</code>, and <code class="font-mono text-xs bg-mustard/20 px-1 py-0.5 border border-mustard rounded">admin whoami</code> for identity verification.</p>
      </div>
      <div>
        <a href="https://github.com/jabarcihuy/bot-wa" target="_blank" class="inline-flex items-center gap-2 px-5 py-2.5 bg-mustard border-3 border-charcoal rounded-lg shadow-brutal-sm text-charcoal font-bold text-sm hover:translate-x-[2px] hover:translate-y-[2px] hover:shadow-none transition-all">
          <i class="fa-brands fa-github text-lg"></i> View Repository
        </a>
      </div>
    </div>`,
  },
]

function showProjectDetail(project) {
  const accentColors = {
    terracotta: 'bg-terracotta',
    sage: 'bg-sage',
    mustard: 'bg-mustard',
  }
  Swal.fire({
    title: project.name,
    html: project.longDescription,
    width: 600,
    confirmButtonText: '<span class="font-mono font-bold tracking-wider"><i class="fa-solid fa-arrow-right mr-2"></i>AWESOME!</span>',
    buttonsStyling: false,
    customClass: {
      popup: 'border-3 border-charcoal rounded-xl shadow-brutal bg-cream',
      title: 'font-heading font-extrabold text-charcoal text-2xl text-left pt-2 pb-4 border-b-3 border-charcoal',
      htmlContainer: 'm-0 pt-4',
      confirmButton: `mt-4 px-8 py-2.5 text-sm border-3 border-charcoal rounded-lg shadow-[4px_4px_0px_rgba(0,0,0,0.8)] font-mono font-bold text-white transition-transform active:translate-y-1 active:translate-x-1 active:shadow-none hover:-translate-y-0.5 hover:-translate-x-0.5 hover:shadow-[6px_6px_0px_rgba(0,0,0,0.8)] ${accentColors[project.accent] || 'bg-terracotta'} text-white`
    },
    background: '#FEF9F2',
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
              : project.accent === 'sage'
                ? 'border-sage shadow-brutal-sage hover:translate-x-[2px] hover:translate-y-[2px] hover:shadow-[3px_3px_0px_var(--color-sage)]'
                : 'border-mustard shadow-brutal-mustard hover:translate-x-[2px] hover:translate-y-[2px] hover:shadow-[3px_3px_0px_var(--color-mustard)]',
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
                  `bg-${project.accent}/10 border-${project.accent} text-${project.accent}`,
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
                    `text-${project.accent}`,
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
                `bg-${project.accent}/8 border-${project.accent}/30 text-${project.accent}`,
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
