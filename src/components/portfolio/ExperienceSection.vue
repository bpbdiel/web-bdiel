<script setup>
import { Briefcase, GraduationCap } from '@lucide/vue'
import { motion } from 'motion-v'

const experience = [
  {
    type: 'work',
    company: 'Tuchi House',
    role: 'Administrador de MultiVende',
    period: '2025 — Actualidad',
    location: 'Remoto, Chile',
    items: [
      'Gestión de catálogo y publicaciones en canales/sellers mediante MultiVende.',
      'Monitoreo y resolución de incidencias operativas asociadas a publicaciones.',
    ],
  },
  {
    type: 'work',
    company: 'Agencia BPL / ELCONTAINER.cl',
    role: 'Marketing Digital / Web',
    period: '2020 — 2024',
    location: 'Remoto, Chile',
    items: [
      'Mantenimiento y actualización de sitios web de clientes.',
      'Apoyo a campañas digitales (Google Ads / RRSS) y operación web.',
    ],
  },
]

const education = [
  {
    institution: 'Universidad Santo Tomás',
    degree: 'Ingeniería Informática (Titulado)',
    period: '2022 — 2025',
    location: 'Temuco, Chile',
    extra: 'Programación Avanzada · Arquitectura de Software · Diseño de Software y Base de Datos',
  },
  {
    institution: 'Liceo Politécnico Pueblo Nuevo',
    degree: 'Técnico en Electrónica',
    period: '2013 — 2016',
    location: 'Temuco, Chile',
    extra: null,
  },
]
</script>

<template>
  <section id="experience" class="bg-muted/30 px-6 py-24">
    <div class="mx-auto max-w-5xl">
      <motion.div
        class="mb-14"
        :initial="{ opacity: 0, y: 20 }"
        :while-in-view="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
      >
        <span class="mb-3 block font-mono text-xs text-blue-500">04 — TRAYECTORIA</span>
        <h2 class="font-heading text-3xl font-bold md:text-4xl">
          Experiencia & Educación
        </h2>
      </motion.div>

      <div class="grid grid-cols-1 gap-12 md:grid-cols-2">
        <div>
          <p class="text-muted-foreground mb-6 font-mono text-[10px] tracking-widest">
            EXPERIENCIA LABORAL
          </p>

          <motion.div
            v-for="(item, index) in experience"
            :key="`${item.company}-${item.period}`"
            class="relative pb-10 pl-8 last:pb-0"
            :initial="{ opacity: 0, x: -20 }"
            :while-in-view="{ opacity: 1, x: 0 }"
            :viewport="{ once: true }"
            :transition="{ delay: index * 0.1 }"
          >
            <div class="absolute bottom-0 left-3 top-3 w-px bg-border last:hidden" />
            <div class="absolute left-0 top-1 flex h-6 w-6 items-center justify-center rounded-full border-2 border-blue-500 bg-blue-50">
              <Briefcase class="h-3 w-3 text-blue-500" />
            </div>

            <div class="glass-panel rounded-xl p-5">
              <div class="mb-1 flex flex-wrap items-start justify-between gap-2">
                <div>
                  <h4 class="font-heading text-base font-bold">
                    {{ item.company }}
                  </h4>
                  <p class="font-body text-muted-foreground text-sm">
                    {{ item.role }}
                  </p>
                </div>
                <div class="text-right">
                  <span class="block font-mono text-xs text-blue-500">{{ item.period }}</span>
                  <span class="text-muted-foreground font-mono text-[10px]">{{ item.location }}</span>
                </div>
              </div>

              <ul class="mt-3 space-y-1">
                <li
                  v-for="detail in item.items"
                  :key="detail"
                  class="flex items-start gap-2"
                >
                  <span class="mt-0.5 flex-shrink-0 text-blue-400">▸</span>
                  <span class="font-body text-muted-foreground text-sm">{{ detail }}</span>
                </li>
              </ul>
            </div>
          </motion.div>
        </div>

        <div>
          <p class="text-muted-foreground mb-6 font-mono text-[10px] tracking-widest">
            EDUCACIÓN
          </p>

          <motion.div
            v-for="(item, index) in education"
            :key="`${item.institution}-${item.period}`"
            class="relative pb-10 pl-8 last:pb-0"
            :initial="{ opacity: 0, x: -20 }"
            :while-in-view="{ opacity: 1, x: 0 }"
            :viewport="{ once: true }"
            :transition="{ delay: index * 0.1 }"
          >
            <div class="absolute bottom-0 left-3 top-3 w-px bg-border last:hidden" />
            <div class="absolute left-0 top-1 flex h-6 w-6 items-center justify-center rounded-full border-2 border-indigo-500 bg-indigo-50">
              <GraduationCap class="h-3 w-3 text-indigo-500" />
            </div>

            <div class="glass-panel rounded-xl p-5">
              <div class="mb-1 flex flex-wrap items-start justify-between gap-2">
                <div>
                  <h4 class="font-heading text-base font-bold">
                    {{ item.institution }}
                  </h4>
                  <p class="font-body text-muted-foreground text-sm">
                    {{ item.degree }}
                  </p>
                </div>
                <div class="text-right">
                  <span class="block font-mono text-xs text-blue-500">{{ item.period }}</span>
                  <span class="text-muted-foreground font-mono text-[10px]">{{ item.location }}</span>
                </div>
              </div>

              <p
                v-if="item.extra"
                class="text-muted-foreground mt-3 font-mono text-[10px] leading-relaxed"
              >
                {{ item.extra }}
              </p>
            </div>
          </motion.div>
        </div>
      </div>
    </div>
  </section>
</template>
