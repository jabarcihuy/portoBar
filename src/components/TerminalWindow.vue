<script setup>
import { ref, onMounted } from 'vue'

const displayedLines = ref([])
const currentLineIndex = ref(0)
const isTyping = ref(false)
const showReplay = ref(false)

const logLines = [
  { type: 'comment', text: '-- Abdul\'s Backend Architecture Schema' },
  { type: 'comment', text: '-- PostgreSQL 15 | Production Database' },
  { type: 'blank', text: '' },
  { type: 'keyword', text: 'CREATE TABLE', rest: ' users (' },
  { type: 'field', text: '  id          SERIAL PRIMARY KEY,' },
  { type: 'field', text: '  email       VARCHAR(255) UNIQUE NOT NULL,' },
  { type: 'field', text: '  password    TEXT NOT NULL,  -- bcrypt hashed' },
  { type: 'field', text: '  role        VARCHAR(20) DEFAULT \'student\',' },
  { type: 'field', text: '  created_at  TIMESTAMPTZ DEFAULT NOW()' },
  { type: 'keyword', text: ');' },
  { type: 'blank', text: '' },
  { type: 'keyword', text: 'CREATE TABLE', rest: ' exam_sessions (' },
  { type: 'field', text: '  id          SERIAL PRIMARY KEY,' },
  { type: 'field', text: '  user_id     INT REFERENCES users(id),' },
  { type: 'field', text: '  score       DECIMAL(5,2),' },
  { type: 'field', text: '  duration_ms INT NOT NULL,' },
  { type: 'field', text: '  status      VARCHAR(20) DEFAULT \'active\',' },
  { type: 'field', text: '  started_at  TIMESTAMPTZ DEFAULT NOW()' },
  { type: 'keyword', text: ');' },
  { type: 'blank', text: '' },
  { type: 'keyword', text: 'CREATE INDEX', rest: ' idx_sessions_user' },
  { type: 'field', text: '  ON exam_sessions(user_id);' },
  { type: 'blank', text: '' },
  { type: 'divider', text: '═══════════════════════════════════════════' },
  { type: 'blank', text: '' },
  { type: 'log', prefix: '[2026-04-23 06:15:01]', level: 'INFO', text: '  Server started on port 3000' },
  { type: 'log', prefix: '[2026-04-23 06:15:01]', level: 'INFO', text: '  Database connected: postgresql://***@db:5432/jebolptn' },
  { type: 'log', prefix: '[2026-04-23 06:15:02]', level: 'INFO', text: '  Redis cache connected: redis://cache:6379' },
  { type: 'log', prefix: '[2026-04-23 06:15:02]', level: 'WARN', text: '  Rate limiter: 100 req/min per IP' },
  { type: 'log', prefix: '[2026-04-23 06:15:03]', level: 'INFO', text: '  Auth middleware initialized (JWT + Refresh Token)' },
  { type: 'log', prefix: '[2026-04-23 06:15:03]', level: 'INFO', text: '  CORS whitelist: [app.jebolptn.com]' },
  { type: 'log', prefix: '[2026-04-23 06:15:04]', level: 'OK', text: '    All systems operational ✓' },
]

function startTyping() {
  if (isTyping.value) return
  isTyping.value = true
  showReplay.value = false
  displayedLines.value = []
  currentLineIndex.value = 0

  const interval = setInterval(() => {
    if (currentLineIndex.value < logLines.length) {
      displayedLines.value.push(logLines[currentLineIndex.value])
      currentLineIndex.value++
    } else {
      clearInterval(interval)
      isTyping.value = false
      showReplay.value = true
    }
  }, 80)
}

function replay() {
  startTyping()
}

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          setTimeout(() => startTyping(), 400)
          observer.disconnect()
        }
      })
    },
    { threshold: 0.15 }
  )

  const el = document.getElementById('terminal')
  if (el) observer.observe(el)
})

const techBadges = [
  { name: 'PostgreSQL', icon: 'fa-solid fa-database' },
  { name: 'Redis', icon: 'fa-solid fa-bolt' },
  { name: 'JWT Auth', icon: 'fa-solid fa-key' },
  { name: 'Rate Limiting', icon: 'fa-solid fa-gauge-high' },
  { name: 'REST API', icon: 'fa-solid fa-plug' },
  { name: 'Docker', icon: 'fa-brands fa-docker' },
]
</script>

<template>
  <section id="terminal" class="py-16 md:py-24 px-5 sm:px-8">
    <div class="max-w-6xl mx-auto">
      <!-- Section header -->
      <div data-aos="fade-up">
        <div class="inline-flex items-center gap-2 px-4 py-2 bg-sage/15 border-3 border-sage rounded-lg shadow-brutal-sm mb-5">
          <i class="fa-solid fa-terminal text-sage"></i>
          <span class="font-mono text-sm text-sage font-medium tracking-wide">The Server Log</span>
        </div>
        <h2 class="font-heading font-extrabold text-charcoal text-3xl sm:text-4xl md:text-5xl leading-tight">
          Under the <span class="text-sage">Hood</span>
        </h2>
        <p class="font-body text-charcoal-muted text-base sm:text-lg mt-3 max-w-2xl mb-10 md:mb-14">
          A peek into the database schemas and server logs that power the platforms.
        </p>
      </div>

      <!-- Terminal window -->
      <div
        data-aos="zoom-in"
        data-aos-duration="800"
        class="border-3 border-charcoal rounded-xl shadow-brutal overflow-hidden"
      >
        <!-- Title bar -->
        <div class="bg-charcoal flex items-center justify-between px-4 sm:px-5 py-3 border-b-3 border-charcoal">
          <div class="flex items-center gap-3">
            <div class="flex gap-2">
              <div class="w-3.5 h-3.5 rounded-full bg-terracotta hover:brightness-125 transition-all cursor-pointer"></div>
              <div class="w-3.5 h-3.5 rounded-full bg-mustard hover:brightness-125 transition-all cursor-pointer"></div>
              <div class="w-3.5 h-3.5 rounded-full bg-sage hover:brightness-125 transition-all cursor-pointer"></div>
            </div>
            <span class="font-mono text-xs sm:text-sm text-cream/50 ml-1">
              <i class="fa-solid fa-terminal mr-1.5"></i>
              abdul@server:~/jebolptn — psql
            </span>
          </div>
          <!-- Replay button -->
          <button
            v-if="showReplay"
            @click="replay"
            class="flex items-center gap-1.5 px-3 py-1 bg-terminal-bg border border-cream/20 rounded-lg text-terminal-green font-mono text-xs hover:bg-cream/10 hover:border-cream/30 transition-all duration-200"
          >
            <i class="fa-solid fa-rotate-right text-[10px]"></i>
            Replay
          </button>
        </div>

        <!-- Terminal body -->
        <div class="bg-terminal-bg p-4 sm:p-6 md:p-8 min-h-[320px] sm:min-h-[400px] max-h-[500px] overflow-y-auto relative">
          <!-- Subtle scan line effect -->
          <div class="absolute inset-0 pointer-events-none" style="background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(255,255,255,0.01) 2px, rgba(255,255,255,0.01) 4px);"></div>

          <div class="font-mono text-xs sm:text-sm leading-relaxed sm:leading-loose relative">
            <div
              v-for="(line, i) in displayedLines"
              :key="i"
              class="animate-slide-in-left whitespace-pre"
              :style="{ animationDelay: `${i * 0.015}s` }"
            >
              <!-- Comment lines -->
              <template v-if="line.type === 'comment'">
                <span class="text-terminal-dim italic">{{ line.text }}</span>
              </template>

              <!-- Blank lines -->
              <template v-else-if="line.type === 'blank'">
                <br />
              </template>

              <!-- Divider -->
              <template v-else-if="line.type === 'divider'">
                <span class="text-terminal-dim/50">{{ line.text }}</span>
              </template>

              <!-- SQL keywords -->
              <template v-else-if="line.type === 'keyword'">
                <span class="text-terminal-yellow font-medium">{{ line.text }}</span>
                <span v-if="line.rest" class="text-terminal-green">{{ line.rest }}</span>
              </template>

              <!-- SQL fields -->
              <template v-else-if="line.type === 'field'">
                <span class="text-terminal-green">{{ line.text }}</span>
              </template>

              <!-- Server log lines -->
              <template v-else-if="line.type === 'log'">
                <span class="text-terminal-dim">{{ line.prefix }}</span>
                <span
                  :class="[
                    'font-medium px-1 rounded mx-1 text-xs',
                    line.level === 'OK' ? 'bg-sage/20 text-sage-light' : line.level === 'WARN' ? 'bg-mustard/20 text-mustard-light' : 'bg-terminal-green/10 text-terminal-green',
                  ]"
                >{{ line.level }}</span>
                <span
                  :class="line.level === 'OK' ? 'text-sage-light font-medium' : 'text-terminal-green'"
                >{{ line.text }}</span>
              </template>
            </div>

            <!-- Cursor -->
            <div class="mt-1 flex items-center">
              <span class="text-terminal-green">abdul@server:~$</span>
              <span class="ml-2 w-2.5 h-5 bg-terminal-green animate-blink inline-block"></span>
            </div>
          </div>
        </div>
      </div>

      <!-- Tech badges below terminal -->
      <div class="flex flex-wrap gap-3 mt-6 justify-center" data-aos="fade-up" data-aos-delay="200">
        <span
          v-for="tech in techBadges"
          :key="tech.name"
          class="inline-flex items-center gap-2 px-3 sm:px-4 py-2 bg-cream border-3 border-charcoal rounded-lg shadow-brutal-sm font-mono text-xs sm:text-sm text-charcoal font-medium hover:translate-x-[1px] hover:translate-y-[1px] hover:shadow-[2px_2px_0px_var(--color-charcoal)] transition-all duration-150 cursor-default tooltip-brutalist"
          :data-tooltip="tech.name"
        >
          <i :class="[tech.icon, 'text-charcoal-muted']"></i>
          {{ tech.name }}
        </span>
      </div>
    </div>
  </section>
</template>
