<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
import { AnimatePresence, motion } from 'motion-v'
import { Menu, Moon, Sun, X } from '@lucide/vue'

const links = [
  { label: 'Sobre mí', href: '#about' },
  { label: 'Skills', href: '#skills' },
  { label: 'Proyectos', href: '#projects' },
  { label: 'Experiencia', href: '#experience' },
  { label: 'Contacto', href: '#contact' },
]

const open = ref(false)
const scrolled = ref(false)
const dark = ref(false)

const onScroll = () => {
  scrolled.value = window.scrollY > 40
}

const go = (href) => {
  open.value = false
  document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' })
}

const applyTheme = (value) => {
  dark.value = value
  document.documentElement.classList.toggle('dark', value)
  localStorage.setItem('theme', value ? 'dark' : 'light')
}

const toggleTheme = () => {
  applyTheme(!dark.value)
}

onMounted(() => {
  const savedTheme = localStorage.getItem('theme')
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches

  applyTheme(savedTheme ? savedTheme === 'dark' : prefersDark)
  onScroll()
  window.addEventListener('scroll', onScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
})
</script>

<template>
  <motion.header
      class="fixed left-0 right-0 top-0 z-50 transition-all duration-500"
      :class="scrolled ? 'glass-panel shadow-sm' : 'bg-transparent'"
      :initial="{ y: -60, opacity: 0 }"
      :animate="{ y: 0, opacity: 1 }"
      :transition="{ duration: 0.5 }"
    >
      <div class="mx-auto flex max-w-5xl items-center justify-between px-6 py-4">
        <button
          type="button"
          class="font-heading text-lg font-bold tracking-tight"
          @click="go('#hero')"
        >
          Bdiel<span class="text-blue-500">.</span>
        </button>

        <nav class="hidden items-center gap-8 md:flex">
          <button
            v-for="link in links"
            :key="link.href"
            type="button"
            class="font-body text-muted-foreground text-sm transition-colors hover:text-blue-600"
            @click="go(link.href)"
          >
            {{ link.label }}
          </button>
        </nav>

        <div class="flex items-center gap-2">
          <button
            type="button"
            class="theme-toggle inline-flex"
            :aria-label="dark ? 'Cambiar a modo claro' : 'Cambiar a modo oscuro'"
            @click="toggleTheme"
          >
            <Sun v-if="dark" class="h-4 w-4" />
            <Moon v-else class="h-4 w-4" />
          </button>

          <button
            type="button"
            class="theme-toggle inline-flex md:hidden"
            aria-label="Abrir menú"
            @click="open = true"
          >
            <Menu class="h-5 w-5" />
          </button>
        </div>
      </div>
  </motion.header>

  <AnimatePresence>
    <motion.div
      v-if="open"
      key="mobile-overlay"
      class="fixed inset-0 z-[60] flex flex-col items-center justify-center gap-8 bg-white/95 backdrop-blur-xl"
      :initial="{ opacity: 0 }"
      :animate="{ opacity: 1 }"
      :exit="{ opacity: 0 }"
    >
      <button
        type="button"
        class="theme-toggle absolute right-6 top-5 inline-flex"
        aria-label="Cerrar menú"
        @click="open = false"
      >
        <X class="h-6 w-6" />
      </button>

      <motion.button
        v-for="(link, index) in links"
        :key="link.href"
        type="button"
        class="font-heading text-3xl font-bold transition-colors hover:text-blue-600"
        :initial="{ opacity: 0, y: 20 }"
        :animate="{ opacity: 1, y: 0 }"
        :transition="{ delay: index * 0.07 }"
        @click="go(link.href)"
      >
        {{ link.label }}
      </motion.button>
    </motion.div>
  </AnimatePresence>
</template>
