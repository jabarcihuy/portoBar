<script setup>
import Swal from 'sweetalert2'

const hardwareProjects = [
  {
    id: 'virtual-pet',
    name: 'ESP32 Virtual Pet',
    description:
      'A Tamagotchi-inspired companion living inside an ESP32 microcontroller — complete with mood states, health meters, and capacitive touch interaction rendered in real-time on a 128x64 OLED display.',
    tags: ['ESP32', 'C++', 'OLED SSD1306', 'Sensors', 'PlatformIO'],
    tagIcons: ['fa-solid fa-microchip', 'fa-solid fa-code', 'fa-solid fa-display', 'fa-solid fa-satellite-dish', 'fa-solid fa-wrench'],
    icon: 'fa-solid fa-paw',
    accent: 'mustard',
    visual: {
      lines: [
        '+-----------------------+',
        '|   ESP32-WROOM-32      |',
        '|  +------------------+ |',
        '|  |  .---.  <3 <3 <3 | |',
        '|  |  | o.o|  HP: 95  | |',
        '|  |  | u  |  LV: 4/5 | |',
        '|  |  \'---\'  HAPPY!   | |',
        '|  +------------------+ |',
        '|  GPIO 21 --> SDA      |',
        '|  GPIO 22 --> SCL      |',
        '+-----------------------+',
      ],
    },
    longDescription: `<div class="text-left font-body">
      <div class="bg-mustard/15 border-3 border-charcoal rounded-xl p-5 mb-6 shadow-brutal-sm relative overflow-hidden">
        <div class="absolute -right-4 -top-4 opacity-10">
          <i class="fa-solid fa-paw text-8xl text-charcoal"></i>
        </div>
        <p class="text-charcoal leading-relaxed text-sm md:text-base relative z-10 font-medium">A nostalgia-driven hardware project that brings the classic virtual pet concept into the modern maker ecosystem. An ESP32 microcontroller drives an SSD1306 OLED display, rendering an animated creature with dynamic mood states driven by real sensor inputs.</p>
      </div>
      <h4 class="font-heading font-extrabold text-charcoal text-lg mb-4 flex items-center gap-3">
        <div class="w-10 h-10 rounded-lg bg-cream-dark border-3 border-charcoal flex items-center justify-center shadow-brutal-sm">
          <i class="fa-solid fa-screwdriver-wrench text-mustard"></i>
        </div>
        Hardware Components
      </h4>
      <ul class="space-y-3 mb-2">
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-mustard hover:bg-mustard/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-microchip text-mustard"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">ESP32-WROOM-32 Development Board</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-mustard hover:bg-mustard/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-display text-mustard"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">SSD1306 128x64 OLED Display via I2C</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-mustard hover:bg-mustard/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-hand-pointer text-mustard"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Capacitive Touch Sensors on GPIO pins</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-mustard hover:bg-mustard/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-volume-high text-mustard"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Passive Buzzer for audio feedback</span>
        </li>
      </ul>
    </div>`,
  },
  {
    id: 'sign-to-speech',
    name: 'Sign-to-Speech Translator',
    description:
      'An assistive technology pipeline that captures Indonesian Sign Language (BISINDO) gestures through a flex-sensor glove, feeds readings into a TensorFlow Lite classifier, and outputs spoken words in real-time — bridging the communication gap for the hearing-impaired.',
    tags: ['Arduino', 'Python', 'TensorFlow Lite', 'Flex Sensors', 'Serial'],
    tagIcons: ['fa-solid fa-microchip', 'fa-brands fa-python', 'fa-solid fa-brain', 'fa-solid fa-hand', 'fa-solid fa-plug'],
    icon: 'fa-solid fa-hands-asl-interpreting',
    accent: 'sage',
    visual: {
      lines: [
        '  +========================+',
        '  |   SIGN-TO-SPEECH v2    |',
        '  +========================+',
        '  |                        |',
        '  |  [GLV] Glove Sensors   |',
        '  |    |                   |',
        '  |    v                   |',
        '  |  [MCU] Arduino Nano    |',
        '  |    | Serial @ 115200   |',
        '  |    v                   |',
        '  |  [ML]  Python Engine   |',
        '  |    | TFLite Model      |',
        '  |    v                   |',
        '  |  [SPK] Speech Output   |',
        '  |                        |',
        '  +========================+',
      ],
    },
    longDescription: `<div class="text-left font-body">
      <div class="bg-sage/15 border-3 border-charcoal rounded-xl p-5 mb-6 shadow-brutal-sm relative overflow-hidden">
        <div class="absolute -right-4 -top-4 opacity-10">
          <i class="fa-solid fa-hands-asl-interpreting text-8xl text-charcoal"></i>
        </div>
        <p class="text-charcoal leading-relaxed text-sm md:text-base relative z-10 font-medium">An end-to-end assistive technology pipeline designed to break communication barriers for the hearing-impaired community in Indonesia. The system captures hand gestures and translates them into audible speech within milliseconds.</p>
      </div>
      <h4 class="font-heading font-extrabold text-charcoal text-lg mb-4 flex items-center gap-3">
        <div class="w-10 h-10 rounded-lg bg-cream-dark border-3 border-charcoal flex items-center justify-center shadow-brutal-sm">
          <i class="fa-solid fa-diagram-project text-sage"></i>
        </div>
        System Architecture
      </h4>
      <ul class="space-y-3 mb-2">
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-sage hover:bg-sage/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-hand text-sage"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">5 precision flex sensors mounted on a custom-fitted glove</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-sage hover:bg-sage/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-microchip text-sage"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Arduino Nano for real-time analog signal acquisition</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-sage hover:bg-sage/5 transition-colors">
          <div class="mt-0.5"><i class="fa-brands fa-python text-sage"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">Python backend running TFLite gesture classifier</span>
        </li>
        <li class="flex items-start gap-3 bg-cream p-3 rounded-lg border-2 border-charcoal/20 hover:border-sage hover:bg-sage/5 transition-colors">
          <div class="mt-0.5"><i class="fa-solid fa-volume-high text-sage"></i></div>
          <span class="text-charcoal-muted text-sm md:text-base font-medium">pyttsx3 engine for natural text-to-speech output</span>
        </li>
      </ul>
    </div>`,
  },
]

function showHardwareDetail(project) {
  Swal.fire({
    title: project.name,
    html: project.longDescription,
    width: 600,
    confirmButtonText: '<span class="font-mono font-bold tracking-wider"><i class="fa-solid fa-check mr-2"></i>COOL!</span>',
    buttonsStyling: false,
    customClass: {
      popup: 'border-3 border-charcoal rounded-xl shadow-brutal bg-cream',
      title: 'font-heading font-extrabold text-charcoal text-2xl text-left pt-2 pb-4 border-b-3 border-charcoal',
      htmlContainer: 'm-0 pt-4',
      confirmButton: `mt-4 px-8 py-2.5 text-sm border-3 border-charcoal rounded-lg shadow-[4px_4px_0px_rgba(0,0,0,0.8)] font-mono font-bold text-white transition-transform active:translate-y-1 active:translate-x-1 active:shadow-none hover:-translate-y-0.5 hover:-translate-x-0.5 hover:shadow-[6px_6px_0px_rgba(0,0,0,0.8)] ${project.accent === 'mustard' ? 'bg-mustard' : 'bg-sage'}`
    },
    background: '#FEF9F2',
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
