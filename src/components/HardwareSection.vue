<script setup>
import Swal from 'sweetalert2'

const hardwareProjects = [
  {
    id: 'virtual-pet',
    name: 'ESP32 Virtual Pet',
    description:
      'An interactive virtual pet running on an ESP32 microcontroller with an OLED display. Features hunger, happiness, and health meters with real sensor inputs for touch-based interaction.',
    tags: ['ESP32', 'C++', 'OLED SSD1306', 'Sensors', 'PlatformIO'],
    tagIcons: ['fa-solid fa-microchip', 'fa-solid fa-code', 'fa-solid fa-display', 'fa-solid fa-satellite-dish', 'fa-solid fa-wrench'],
    icon: 'fa-solid fa-paw',
    accent: 'mustard',
    visual: {
      lines: [
        '┌──────────────────────┐',
        '│   ESP32-WROOM-32     │',
        '│  ┌─────────────────┐ │',
        '│  │  ╭───╮  ♥ ♥ ♥  │ │',
        '│  │  │ o.o│  HP: 95 │ │',
        '│  │  │ ᴗ  │  ★★★★☆ │ │',
        '│  │  ╰───╯  HAPPY!  │ │',
        '│  └─────────────────┘ │',
        '│  GPIO 21 ──► SDA     │',
        '│  GPIO 22 ──► SCL     │',
        '└──────────────────────┘',
      ],
    },
    longDescription: `<div style="text-align: left; font-family: 'Inter', sans-serif;">
      <p style="color: #5D6D7E; margin-bottom: 12px;">A nostalgic Tamagotchi-inspired virtual pet running on real hardware. The ESP32 drives an SSD1306 OLED display showing an animated pet with multiple mood states.</p>
      <h4 style="font-family: 'Plus Jakarta Sans'; color: #2C3E50; margin-bottom: 8px;">🔧 Hardware Components</h4>
      <ul style="color: #5D6D7E; padding-left: 20px; margin-bottom: 12px;">
        <li>ESP32-WROOM-32 Dev Board</li>
        <li>SSD1306 128x64 OLED Display (I2C)</li>
        <li>Capacitive Touch Sensors (GPIO)</li>
        <li>Passive Buzzer for sound effects</li>
      </ul>
    </div>`,
  },
  {
    id: 'sign-to-speech',
    name: 'Sign-to-Speech Translator',
    description:
      'A computer vision system that translates Indonesian Sign Language (BISINDO) to audible speech in real-time. Uses flex sensors on a glove connected to an Arduino, with a Python ML backend.',
    tags: ['Arduino', 'Python', 'TensorFlow Lite', 'Flex Sensors', 'Serial'],
    tagIcons: ['fa-solid fa-microchip', 'fa-brands fa-python', 'fa-solid fa-brain', 'fa-solid fa-hand', 'fa-solid fa-plug'],
    icon: 'fa-solid fa-hands-asl-interpreting',
    accent: 'sage',
    visual: {
      lines: [
        '  ╔═══════════════════════╗',
        '  ║   SIGN-TO-SPEECH v2   ║',
        '  ╠═══════════════════════╣',
        '  ║                       ║',
        '  ║  🧤 Glove Sensors     ║',
        '  ║    │                   ║',
        '  ║    ▼                   ║',
        '  ║  📡 Arduino Nano      ║',
        '  ║    │ Serial @ 115200   ║',
        '  ║    ▼                   ║',
        '  ║  🐍 Python ML Engine  ║',
        '  ║    │ TFLite Model      ║',
        '  ║    ▼                   ║',
        '  ║  🔊 Speech Output     ║',
        '  ║                       ║',
        '  ╚═══════════════════════╝',
      ],
    },
    longDescription: `<div style="text-align: left; font-family: 'Inter', sans-serif;">
      <p style="color: #5D6D7E; margin-bottom: 12px;">An assistive technology project bridging communication gaps for the hearing-impaired community in Indonesia by translating BISINDO gestures to spoken words.</p>
      <h4 style="font-family: 'Plus Jakarta Sans'; color: #2C3E50; margin-bottom: 8px;">🔧 System Architecture</h4>
      <ul style="color: #5D6D7E; padding-left: 20px; margin-bottom: 12px;">
        <li>5 flex sensors on a custom glove</li>
        <li>Arduino Nano for analog reading</li>
        <li>Python backend with TFLite classifier</li>
        <li>pyttsx3 for text-to-speech output</li>
      </ul>
    </div>`,
  },
]

function showHardwareDetail(project) {
  Swal.fire({
    title: project.name,
    html: project.longDescription,
    width: 560,
    confirmButtonText: '<i class="fa-solid fa-check"></i> Cool!',
    confirmButtonColor: project.accent === 'mustard' ? '#D4A843' : '#7D9B76',
  })
}
</script>

<template>
  <section id="hardware" class="py-16 md:py-24 px-5 sm:px-8 bg-cream-dark">
    <div class="max-w-6xl mx-auto">
      <!-- Section header -->
      <div data-aos="fade-up">
        <div class="inline-flex items-center gap-2 px-4 py-2 bg-mustard/15 border-3 border-mustard rounded-lg shadow-brutal-sm mb-5">
          <i class="fa-solid fa-microchip text-mustard"></i>
          <span class="font-mono text-sm text-mustard font-medium tracking-wide">Hardware & Embedded</span>
        </div>
        <h2 class="font-heading font-extrabold text-charcoal text-3xl sm:text-4xl md:text-5xl leading-tight">
          Beyond the <span class="text-mustard">Server</span>
        </h2>
        <p class="font-body text-charcoal-muted text-base sm:text-lg mt-3 max-w-2xl mb-10 md:mb-14">
          Microcontrollers, sensors, and Python — bridging software with the physical world.
        </p>
      </div>

      <!-- Hardware cards grid -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 md:gap-8">
        <div
          v-for="(project, index) in hardwareProjects"
          :key="project.id"
          :data-aos="index === 0 ? 'fade-right' : 'fade-left'"
          :data-aos-delay="index * 100"
          class="group bg-cream border-3 border-charcoal rounded-xl shadow-brutal card-interactive overflow-hidden cursor-pointer"
          @click="showHardwareDetail(project)"
        >
          <!-- Visual placeholder (ASCII art terminal) -->
          <div class="bg-terminal-bg p-4 sm:p-5 border-b-3 border-charcoal relative">
            <!-- Shimmer overlay -->
            <div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 animate-shimmer pointer-events-none"></div>

            <!-- Mini terminal bar -->
            <div class="flex items-center gap-2 mb-3">
              <div class="w-3 h-3 rounded-full bg-terracotta/80"></div>
              <div class="w-3 h-3 rounded-full bg-mustard/80"></div>
              <div class="w-3 h-3 rounded-full bg-sage/80"></div>
              <span class="font-mono text-xs text-terminal-dim ml-2">
                <i class="fa-solid fa-file-code mr-1"></i>
                {{ project.name.toLowerCase().replace(/\s/g, '_') }}.ino
              </span>
            </div>
            <!-- ASCII visual -->
            <pre class="font-mono text-xs sm:text-sm text-terminal-green leading-relaxed overflow-x-auto"><code><template v-for="(line, i) in project.visual.lines" :key="i">{{ line }}
</template></code></pre>
          </div>

          <!-- Card body -->
          <div class="p-5 sm:p-6">
            <div class="flex items-center gap-3 mb-3">
              <div
                :class="[
                  'w-10 h-10 border-3 rounded-lg flex items-center justify-center transition-transform duration-300 group-hover:scale-110 group-hover:rotate-6',
                  `bg-${project.accent}/15 border-${project.accent} text-${project.accent}`,
                ]"
              >
                <i :class="project.icon"></i>
              </div>
              <h3 class="font-heading font-extrabold text-charcoal text-lg sm:text-xl flex items-center gap-2">
                {{ project.name }}
                <i class="fa-solid fa-arrow-up-right-from-square text-xs text-charcoal-faint group-hover:text-charcoal-muted transition-colors"></i>
              </h3>
            </div>

            <p class="font-body text-charcoal-muted text-sm sm:text-base leading-relaxed mb-4">
              {{ project.description }}
            </p>

            <!-- Tags -->
            <div class="flex flex-wrap gap-2 mb-3">
              <span
                v-for="(tag, ti) in project.tags"
                :key="tag"
                :class="[
                  'inline-flex items-center gap-1.5 px-2.5 py-1 border rounded text-xs font-mono font-medium hover:scale-105 transition-transform duration-200',
                  `bg-${project.accent}/10 border-${project.accent}/40 text-${project.accent}`,
                ]"
              >
                <i :class="[project.tagIcons[ti], 'text-[10px]']"></i>
                {{ tag }}
              </span>
            </div>

            <!-- Click hint -->
            <div class="pt-3 border-t border-charcoal/10 flex items-center gap-2 text-xs font-mono text-charcoal-faint group-hover:text-charcoal-muted transition-colors">
              <i class="fa-solid fa-hand-pointer"></i>
              <span>Click to explore</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
