<script setup>
import { motion } from 'motion-v'
import { ArrowDown, Mail, MapPin } from '@lucide/vue'
import heroImage from '../../assets/image.png'

const go = (href) => {
  document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <section id="hero" class="flex min-h-screen flex-col justify-center px-6 pb-12 pt-20">
    <div class="mx-auto w-full max-w-5xl">
      <div class="grid grid-cols-1 items-center gap-12 md:grid-cols-2">
        <div>
          <motion.p
            class="mb-4 font-mono text-xs tracking-widest text-blue-500"
            :initial="{ opacity: 0, y: 10 }"
            :animate="{ opacity: 1, y: 0 }"
            :transition="{ delay: 0.1 }"
          >
            ¡Hola, mundo! 👋
          </motion.p>

          <motion.h1
            class="font-heading mb-4 text-4xl font-bold leading-tight md:text-6xl"
            :initial="{ opacity: 0, y: 30 }"
            :animate="{ opacity: 1, y: 0 }"
            :transition="{ delay: 0.2, duration: 0.6 }"
          >
            Pedro<br>
            Barra<br>
            <span class="text-gradient">Pino</span>
          </motion.h1>

          <motion.p
            class="font-body text-muted-foreground mb-2 text-lg"
            :initial="{ opacity: 0, y: 20 }"
            :animate="{ opacity: 1, y: 0 }"
            :transition="{ delay: 0.35 }"
          >
            Ingeniero Informático · Desarrollador Junior
          </motion.p>

          <motion.p
            class="font-body text-muted-foreground mb-8 max-w-sm text-sm leading-relaxed"
            :initial="{ opacity: 0, y: 20 }"
            :animate="{ opacity: 1, y: 0 }"
            :transition="{ delay: 0.45 }"
          >
            Apasionado por construir plataformas web funcionales con Django y Python.
            Titulado en Ingeniería Informática, con experiencia real en proyectos de automatización y gestión.
          </motion.p>

          <motion.div
            class="mb-8 flex flex-wrap gap-3"
            :initial="{ opacity: 0, y: 20 }"
            :animate="{ opacity: 1, y: 0 }"
            :transition="{ delay: 0.55 }"
          >
            <button
              type="button"
              class="font-body rounded-full bg-blue-600 px-6 py-3 text-sm font-medium text-white transition-all hover:bg-blue-700 hover:shadow-lg hover:shadow-blue-200"
              @click="go('#contact')"
            >
              Contáctame
            </button>
            <button
              type="button"
              class="font-body border-border hover:bg-foreground hover:text-background rounded-full border px-6 py-3 text-sm font-medium transition-all"
              @click="go('#projects')"
            >
              Ver proyectos
            </button>
          </motion.div>

          <motion.div
            class="flex flex-wrap items-center gap-4"
            :initial="{ opacity: 0 }"
            :animate="{ opacity: 1 }"
            :transition="{ delay: 0.7 }"
          >
            <a
              href="https://github.com/iabdielll"
              target="_blank"
              rel="noopener noreferrer"
              class="text-muted-foreground hover:text-foreground flex items-center gap-2 text-sm transition-colors"
            >
              <svg
                class="h-4 w-4"
                viewBox="0 0 24 24"
                fill="currentColor"
                aria-hidden="true"
              >
                <path d="M12 2C6.48 2 2 6.58 2 12.26c0 4.53 2.87 8.37 6.84 9.73.5.1.68-.22.68-.49 0-.24-.01-1.05-.01-1.9-2.78.62-3.37-1.22-3.37-1.22-.45-1.19-1.11-1.5-1.11-1.5-.91-.64.07-.63.07-.63 1 .07 1.53 1.06 1.53 1.06.9 1.57 2.36 1.12 2.93.85.09-.67.35-1.12.64-1.38-2.22-.26-4.56-1.14-4.56-5.07 0-1.12.39-2.03 1.03-2.75-.1-.26-.45-1.3.1-2.71 0 0 .84-.28 2.75 1.05A9.38 9.38 0 0 1 12 6.96c.85 0 1.7.12 2.5.34 1.91-1.33 2.75-1.05 2.75-1.05.55 1.41.2 2.45.1 2.71.64.72 1.03 1.63 1.03 2.75 0 3.94-2.34 4.81-4.57 5.07.36.32.68.94.68 1.9 0 1.37-.01 2.47-.01 2.82 0 .27.18.59.69.49A10.08 10.08 0 0 0 22 12.26C22 6.58 17.52 2 12 2Z" />
              </svg>
              <span class="font-mono text-xs">iabdielll</span>
            </a>
            <a
              href="mailto:abdielbarrapino@gmail.com"
              class="text-muted-foreground flex items-center gap-2 text-sm transition-colors hover:text-blue-600"
            >
              <Mail class="h-4 w-4" />
              <span class="font-mono text-xs">abdielbarrapino@gmail.com</span>
            </a>
            <span class="text-muted-foreground flex items-center gap-2 text-sm">
              <MapPin class="h-4 w-4" />
              <span class="font-mono text-xs">Temuco, Chile</span>
            </span>
          </motion.div>
        </div>

        <motion.div
          class="flex justify-center"
          :initial="{ opacity: 0, scale: 0.9 }"
          :animate="{ opacity: 1, scale: 1 }"
          :transition="{ delay: 0.4, duration: 0.6 }"
        >
          <div class="relative">
            <div class="absolute -inset-4 animate-pulse rounded-full bg-gradient-to-br from-blue-100 to-blue-50" />
            <div class="relative h-56 w-56 overflow-hidden rounded-full bg-gradient-to-br from-blue-600 to-blue-400 p-1 shadow-2xl shadow-blue-200 md:h-72 md:w-72">
              <img
                :src="heroImage"
                alt="Pedro Barra Pino"
                class="h-full w-full rounded-full object-cover"
              >
            </div>
            <div class="glass-panel absolute -bottom-3 left-1/2 -translate-x-1/2 whitespace-nowrap rounded-full px-5 py-2 shadow-md">
              <span class="font-mono text-xs font-medium text-blue-600">Disponible para trabajar ✓</span>
            </div>
          </div>
        </motion.div>
      </div>
    </div>

    <motion.div
      class="mt-16 flex justify-center"
      :initial="{ opacity: 0 }"
      :animate="{ opacity: 1 }"
      :transition="{ delay: 1.2 }"
    >
      <motion.div
        class="text-muted-foreground flex flex-col items-center gap-1"
        :animate="{ y: [0, 8, 0] }"
        :transition="{ repeat: Infinity, duration: 1.6 }"
      >
        <span class="font-mono text-[10px] tracking-widest">SCROLL</span>
        <ArrowDown class="h-4 w-4" />
      </motion.div>
    </motion.div>
  </section>
</template>
