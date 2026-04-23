<script setup>
import { ref } from 'vue'
import Swal from 'sweetalert2'

const formData = ref({
  name: '',
  email: '',
  message: '',
})
const isSending = ref(false)

async function handleSubmit() {
  if (!formData.value.name || !formData.value.email || !formData.value.message) {
    Swal.fire({
      icon: 'warning',
      title: 'Missing Fields',
      text: 'Please fill in all fields before sending.',
      confirmButtonText: '<i class="fa-solid fa-pen"></i> Got it',
      confirmButtonColor: '#D4A843',
    })
    return
  }

  // Email validation
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  if (!emailRegex.test(formData.value.email)) {
    Swal.fire({
      icon: 'error',
      title: 'Invalid Email',
      text: 'Please enter a valid email address.',
      confirmButtonText: '<i class="fa-solid fa-check"></i> Fix it',
      confirmButtonColor: '#C0755A',
    })
    return
  }

  isSending.value = true

  // Simulate sending
  await new Promise((resolve) => setTimeout(resolve, 1500))

  isSending.value = false
  formData.value = { name: '', email: '', message: '' }

  Swal.fire({
    icon: 'success',
    title: 'Message Sent!',
    html: '<p style="color: #5D6D7E;">Thanks for reaching out! I\'ll get back to you as soon as possible. <strong>Keep building awesome things!</strong></p>',
    confirmButtonText: '<i class="fa-solid fa-thumbs-up"></i> Awesome!',
    confirmButtonColor: '#7D9B76',
    timer: 5000,
    timerProgressBar: true,
  })
}

const contactMethods = [
  {
    icon: 'fa-brands fa-github',
    label: 'GitHub',
    value: 'github.com/jabarcihuy',
    href: 'https://github.com/jabarcihuy',
    accent: 'charcoal',
  },
  {
    icon: 'fa-brands fa-linkedin-in',
    label: 'LinkedIn',
    value: 'Coming Soon',
    href: '#',
    accent: 'sage',
  },
  {
    icon: 'fa-solid fa-envelope',
    label: 'Email',
    value: 'abduljabarbrngkl@gmail.com',
    href: 'mailto:abduljabarbrngkl@gmail.com',
    accent: 'terracotta',
  },
]
</script>

<template>
  <section id="contact" class="py-16 md:py-24 px-5 sm:px-8 bg-cream-dark">
    <div class="max-w-6xl mx-auto">
      <!-- Section header -->
      <div data-aos="fade-up" class="text-center mb-10 md:mb-14">
        <div class="inline-flex items-center gap-2 px-4 py-2 bg-rose/15 border-3 border-rose rounded-lg shadow-brutal-sm mb-5">
          <i class="fa-solid fa-paper-plane text-rose"></i>
          <span class="font-mono text-sm text-rose font-medium tracking-wide">Get In Touch</span>
        </div>
        <h2 class="font-heading font-extrabold text-charcoal text-3xl sm:text-4xl md:text-5xl leading-tight">
          Let's <span class="text-rose">Connect</span>
        </h2>
        <p class="font-body text-charcoal-muted text-base sm:text-lg mt-3 max-w-xl mx-auto">
          Have a project idea or just want to say hello? Drop me a message!
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-5 gap-8">
        <!-- Contact form -->
        <div class="lg:col-span-3" data-aos="fade-right">
          <form @submit.prevent="handleSubmit" class="bg-cream border-3 border-charcoal rounded-xl shadow-brutal p-6 sm:p-8">
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 mb-4">
              <!-- Name -->
              <div>
                <label class="block font-heading font-bold text-charcoal text-sm mb-2">
                  <i class="fa-solid fa-user mr-1.5 text-charcoal-muted"></i>Name
                </label>
                <input
                  v-model="formData.name"
                  type="text"
                  placeholder="Your name"
                  class="w-full px-4 py-3 bg-cream border-3 border-charcoal rounded-lg font-body text-sm text-charcoal placeholder:text-charcoal-faint focus:outline-none focus:border-terracotta focus:shadow-[3px_3px_0px_var(--color-terracotta)] transition-all duration-200"
                />
              </div>
              <!-- Email -->
              <div>
                <label class="block font-heading font-bold text-charcoal text-sm mb-2">
                  <i class="fa-solid fa-at mr-1.5 text-charcoal-muted"></i>Email
                </label>
                <input
                  v-model="formData.email"
                  type="email"
                  placeholder="you@example.com"
                  class="w-full px-4 py-3 bg-cream border-3 border-charcoal rounded-lg font-body text-sm text-charcoal placeholder:text-charcoal-faint focus:outline-none focus:border-terracotta focus:shadow-[3px_3px_0px_var(--color-terracotta)] transition-all duration-200"
                />
              </div>
            </div>
            <!-- Message -->
            <div class="mb-5">
              <label class="block font-heading font-bold text-charcoal text-sm mb-2">
                <i class="fa-solid fa-comment-dots mr-1.5 text-charcoal-muted"></i>Message
              </label>
              <textarea
                v-model="formData.message"
                rows="5"
                placeholder="Tell me about your project or idea..."
                class="w-full px-4 py-3 bg-cream border-3 border-charcoal rounded-lg font-body text-sm text-charcoal placeholder:text-charcoal-faint focus:outline-none focus:border-terracotta focus:shadow-[3px_3px_0px_var(--color-terracotta)] transition-all duration-200 resize-none"
              ></textarea>
            </div>
            <!-- Submit -->
            <button
              type="submit"
              :disabled="isSending"
              :class="[
                'w-full sm:w-auto inline-flex items-center justify-center gap-2.5 px-8 py-3.5 font-heading font-bold text-sm border-3 border-charcoal rounded-lg transition-all duration-150',
                isSending
                  ? 'bg-charcoal-muted text-cream cursor-wait shadow-none'
                  : 'bg-terracotta text-cream shadow-brutal hover:shadow-brutal-pressed hover:translate-x-[2px] hover:translate-y-[2px] active:translate-x-[4px] active:translate-y-[4px] active:shadow-none',
              ]"
            >
              <i :class="isSending ? 'fa-solid fa-spinner fa-spin' : 'fa-solid fa-paper-plane'"></i>
              <span>{{ isSending ? 'Sending...' : 'Send Message' }}</span>
            </button>
          </form>
        </div>

        <!-- Contact methods -->
        <div class="lg:col-span-2 flex flex-col gap-4" data-aos="fade-left" data-aos-delay="150">
          <a
            v-for="method in contactMethods"
            :key="method.label"
            :href="method.href"
            class="group bg-cream border-3 border-charcoal rounded-xl shadow-brutal p-5 flex items-center gap-4 card-interactive"
          >
            <div class="w-12 h-12 border-3 border-charcoal rounded-lg bg-charcoal/5 flex items-center justify-center group-hover:bg-terracotta/10 group-hover:border-terracotta transition-all duration-200">
              <i :class="[method.icon, 'text-lg text-charcoal-muted group-hover:text-terracotta transition-colors duration-200']"></i>
            </div>
            <div>
              <p class="font-heading font-bold text-charcoal text-sm">{{ method.label }}</p>
              <p class="font-mono text-xs text-charcoal-muted">{{ method.value }}</p>
            </div>
            <i class="fa-solid fa-arrow-right text-xs text-charcoal-faint group-hover:text-terracotta ml-auto transition-all duration-200 group-hover:translate-x-1"></i>
          </a>

          <!-- Availability badge -->
          <div class="bg-sage/10 border-3 border-sage rounded-xl p-5 mt-2">
            <div class="flex items-center gap-3 mb-2">
              <div class="relative">
                <div class="w-3 h-3 bg-sage rounded-full"></div>
                <div class="w-3 h-3 bg-sage rounded-full absolute inset-0 animate-ping opacity-50"></div>
              </div>
              <p class="font-heading font-bold text-sage text-sm">Available for Projects</p>
            </div>
            <p class="font-body text-charcoal-muted text-xs leading-relaxed">
              Currently open to freelance work, collaborations, and interesting backend challenges.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
