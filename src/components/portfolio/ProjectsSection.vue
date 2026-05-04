<script setup>
import { ref } from 'vue'
import { motion } from 'motion-v'
import { ChevronDown, ChevronUp } from '@lucide/vue'

const projects = [
  {
    title: 'Automatización de Documentos Administrativos',
    subtitle: 'Proyecto de Título — Colegio Alenkura',
    year: '2025',
    stack: ['Django', 'Python', 'MySQL', 'HTML/CSS', 'Git'],
    description: [
      'Plataforma web para automatizar la gestión y generación de documentos administrativos del colegio.',
      'Modelé datos y flujos para reducir tareas manuales y estandarizar información para uso administrativo.',
      'Administré la solución y realicé mejoras iterativas según requerimientos operativos reales.',
    ],
    color: 'from-blue-600 to-blue-400',
    letter: 'A',
  },
  {
    title: 'Plataforma Registro de Visitas + Reportes',
    subtitle: 'Práctica Profesional — Colegio Bautista',
    year: '2025',
    stack: ['Django', 'Python', 'SQLite', 'HTML/CSS', 'Git'],
    description: [
      'Sistema de registro y control de visitas con funciones de ingreso/salida, historial y búsqueda.',
      'Generación de reportes con filtros por fechas y criterios para apoyo administrativo.',
      'Diseño de modelos y pantallas enfocadas en trazabilidad del proceso completo.',
    ],
    color: 'from-indigo-600 to-indigo-400',
    letter: 'B',
  },
]

const expanded = ref(null)

const toggleProject = (index) => {
  expanded.value = expanded.value === index ? null : index
}
</script>

<template>
  <section id="projects" class="px-6 py-24">
    <div class="mx-auto max-w-5xl">
      <motion.div
        class="mb-14"
        :initial="{ opacity: 0, y: 20 }"
        :while-in-view="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
      >
        <span class="mb-3 block font-mono text-xs text-blue-500">03 — PROYECTOS</span>
        <h2 class="font-heading text-3xl font-bold md:text-4xl">
          Lo que he construido
        </h2>
      </motion.div>

      <div class="grid grid-cols-1 gap-6 md:grid-cols-2">
        <motion.div
          v-for="(project, index) in projects"
          :key="project.title"
          class="group overflow-hidden rounded-2xl border border-border bg-white transition-all duration-400 hover:shadow-xl hover:shadow-blue-100"
          :initial="{ opacity: 0, y: 40 }"
          :while-in-view="{ opacity: 1, y: 0 }"
          :viewport="{ once: true }"
          :transition="{ delay: index * 0.12 }"
        >
          <div
            class="flex items-end justify-between bg-gradient-to-br p-8"
            :class="project.color"
          >
            <span class="font-heading select-none text-7xl font-bold leading-none text-white/20">
              {{ project.letter }}
            </span>
            <span class="font-mono text-xs text-white/60">{{ project.year }}</span>
          </div>

          <div class="p-6">
            <p class="text-muted-foreground mb-1 font-mono text-[10px]">
              {{ project.subtitle }}
            </p>
            <h3 class="font-heading mb-4 text-lg font-bold leading-tight">
              {{ project.title }}
            </h3>

            <div class="mb-4 flex flex-wrap gap-2">
              <span
                v-for="stackItem in project.stack"
                :key="`${project.title}-${stackItem}`"
                class="bg-muted border-border text-muted-foreground rounded-full border px-3 py-1 font-mono text-[10px]"
              >
                {{ stackItem }}
              </span>
            </div>

            <button
              type="button"
              class="font-body mb-3 flex items-center gap-1 text-xs text-blue-600 transition-colors hover:text-blue-800"
              @click="toggleProject(index)"
            >
              {{ expanded === index ? 'Ver menos' : 'Ver detalle' }}
              <ChevronUp v-if="expanded === index" class="h-3 w-3" />
              <ChevronDown v-else class="h-3 w-3" />
            </button>

            <motion.ul
              v-if="expanded === index"
              class="space-y-2"
              :initial="{ opacity: 0, height: 0 }"
              :animate="{ opacity: 1, height: 'auto' }"
            >
              <li
                v-for="detail in project.description"
                :key="detail"
                class="flex items-start gap-2"
              >
                <span class="mt-1 flex-shrink-0 text-blue-400">▸</span>
                <span class="font-body text-muted-foreground text-sm leading-relaxed">
                  {{ detail }}
                </span>
              </li>
            </motion.ul>
          </div>
        </motion.div>
      </div>

      <motion.div
        class="mt-10 text-center"
        :initial="{ opacity: 0, y: 20 }"
        :while-in-view="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
      >
        <a
          href="https://github.com/iabdielll"
          target="_blank"
          rel="noopener noreferrer"
          class="font-body text-muted-foreground border-border hover:bg-foreground hover:text-background inline-flex items-center gap-2 rounded-full border px-6 py-3 text-sm transition-all"
        >
          <svg
            class="h-4 w-4"
            viewBox="0 0 24 24"
            fill="currentColor"
            aria-hidden="true"
          >
            <path d="M12 2C6.48 2 2 6.58 2 12.26c0 4.53 2.87 8.37 6.84 9.73.5.1.68-.22.68-.49 0-.24-.01-1.05-.01-1.9-2.78.62-3.37-1.22-3.37-1.22-.45-1.19-1.11-1.5-1.11-1.5-.91-.64.07-.63.07-.63 1 .07 1.53 1.06 1.53 1.06.9 1.57 2.36 1.12 2.93.85.09-.67.35-1.12.64-1.38-2.22-.26-4.56-1.14-4.56-5.07 0-1.12.39-2.03 1.03-2.75-.1-.26-.45-1.3.1-2.71 0 0 .84-.28 2.75 1.05A9.38 9.38 0 0 1 12 6.96c.85 0 1.7.12 2.5.34 1.91-1.33 2.75-1.05 2.75-1.05.55 1.41.2 2.45.1 2.71.64.72 1.03 1.63 1.03 2.75 0 3.94-2.34 4.81-4.57 5.07.36.32.68.94.68 1.9 0 1.37-.01 2.47-.01 2.82 0 .27.18.59.69.49A10.08 10.08 0 0 0 22 12.26C22 6.58 17.52 2 12 2Z" />
          </svg>
          Ver más en GitHub
        </a>
      </motion.div>
    </div>
  </section>
</template>
