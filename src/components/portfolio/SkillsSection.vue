<script setup>
import { motion } from 'motion-v'

const skillGroups = [
  {
    category: 'Backend',
    color: 'bg-blue-50 border-blue-100',
    accent: 'text-blue-600',
    skills: ['Django', 'Python'],
  },
  {
    category: 'Lenguajes',
    color: 'bg-indigo-50 border-indigo-100',
    accent: 'text-indigo-600',
    skills: ['Python', 'JavaScript', 'Java', 'C#'],
  },
  {
    category: 'Bases de Datos',
    color: 'bg-sky-50 border-sky-100',
    accent: 'text-sky-600',
    skills: ['MySQL', 'SQLite'],
  },
  {
    category: 'Frontend / Web',
    color: 'bg-cyan-50 border-cyan-100',
    accent: 'text-cyan-600',
    skills: ['HTML5', 'CSS3'],
  },
  {
    category: 'Herramientas',
    color: 'bg-slate-50 border-slate-200',
    accent: 'text-slate-600',
    skills: ['Git', 'GitHub', 'Linux', 'macOS', 'Windows'],
  },
  {
    category: 'Metodologías',
    color: 'bg-violet-50 border-violet-100',
    accent: 'text-violet-600',
    skills: ['Scrum', 'Agile'],
  },
]

const softSkills = [
  'Trabajo en equipo',
  'Proactividad',
  'Comunicación',
  'Aprendizaje continuo',
  'Orientación a solución de problemas',
]
</script>

<template>
  <section id="skills" class="bg-muted/30 px-6 py-24">
    <div class="mx-auto max-w-5xl">
      <motion.div
        class="mb-14"
        :initial="{ opacity: 0, y: 20 }"
        :while-in-view="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
      >
        <span class="mb-3 block font-mono text-xs text-blue-500">02 — HABILIDADES</span>
        <h2 class="font-heading text-3xl font-bold md:text-4xl">
          Stack Técnico
        </h2>
      </motion.div>

      <div class="mb-12 grid grid-cols-1 gap-5 sm:grid-cols-2 md:grid-cols-3">
        <motion.div
          v-for="(group, index) in skillGroups"
          :key="group.category"
          class="rounded-2xl border p-5"
          :class="group.color"
          :initial="{ opacity: 0, y: 30 }"
          :while-in-view="{ opacity: 1, y: 0 }"
          :viewport="{ once: true }"
          :transition="{ delay: index * 0.08 }"
        >
          <span
            class="mb-3 block font-mono text-[10px] font-medium tracking-widest"
            :class="group.accent"
          >
            {{ group.category.toUpperCase() }}
          </span>

          <div class="flex flex-wrap gap-2">
            <span
              v-for="skill in group.skills"
              :key="`${group.category}-${skill}`"
              class="font-body text-foreground rounded-full border border-white/60 bg-white/80 px-3 py-1.5 text-xs shadow-sm"
            >
              {{ skill }}
            </span>
          </div>
        </motion.div>
      </div>

      <motion.div
        :initial="{ opacity: 0, y: 20 }"
        :while-in-view="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
      >
        <span class="text-muted-foreground mb-4 block font-mono text-[10px] tracking-widest">
          HABILIDADES BLANDAS
        </span>

        <div class="flex flex-wrap gap-3">
          <span
            v-for="skill in softSkills"
            :key="skill"
            class="font-body border-border text-muted-foreground rounded-full border bg-white px-4 py-2 text-sm"
          >
            {{ skill }}
          </span>
        </div>
      </motion.div>
    </div>
  </section>
</template>
