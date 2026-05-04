<script setup>
import { reactive, ref } from 'vue'
import { CheckCircle2, Mail, MapPin, Phone, Send } from '@lucide/vue'
import { motion } from 'motion-v'

const info = [
  { icon: Mail, label: 'Email', value: 'abdielbarrapino@gmail.com', href: 'mailto:abdielbarrapino@gmail.com' },
  { icon: Phone, label: 'Teléfono', value: '+56 9 5816 3034', href: 'tel:+56958163034' },
  { icon: 'github', label: 'GitHub', value: 'github.com/iabdielll', href: 'https://github.com/iabdielll' },
  { icon: MapPin, label: 'Ubicación', value: 'Temuco, Chile', href: null },
]

const fields = [
  { label: 'Nombre', key: 'name', type: 'text', required: true },
  { label: 'Email', key: 'email', type: 'email', required: true },
]

const form = reactive({
  name: '',
  email: '',
  message: '',
})

const sent = ref(false)
const sending = ref(false)

const set = (key, value) => {
  form[key] = value
}

const handleSubmit = async () => {
  sending.value = true
  await new Promise((resolve) => setTimeout(resolve, 1200))
  sending.value = false
  sent.value = true
}
</script>

<template>
  <section id="contact" class="px-6 py-24">
    <div class="mx-auto max-w-5xl">
      <motion.div
        class="mb-14"
        :initial="{ opacity: 0, y: 20 }"
        :while-in-view="{ opacity: 1, y: 0 }"
        :viewport="{ once: true }"
      >
        <span class="mb-3 block font-mono text-xs text-blue-500">05 — CONTACTO</span>
        <h2 class="font-heading text-3xl font-bold md:text-4xl">
          Trabajemos juntos
        </h2>
        <p class="font-body text-muted-foreground mt-3 max-w-md">
          ¿Tienes un proyecto en mente? Escríbeme y conversamos.
        </p>
      </motion.div>

      <div class="grid grid-cols-1 items-start gap-12 md:grid-cols-2">
        <motion.div
          class="space-y-5"
          :initial="{ opacity: 0, x: -20 }"
          :while-in-view="{ opacity: 1, x: 0 }"
          :viewport="{ once: true }"
        >
          <div
            v-for="item in info"
            :key="item.label"
            class="group flex items-center gap-4"
          >
            <div class="border-border flex h-11 w-11 items-center justify-center rounded-xl border bg-white transition-all group-hover:border-blue-600 group-hover:bg-blue-600">
              <svg
                v-if="item.icon === 'github'"
                class="text-muted-foreground h-4 w-4 transition-colors group-hover:text-white"
                viewBox="0 0 24 24"
                fill="currentColor"
                aria-hidden="true"
              >
                <path d="M12 2C6.48 2 2 6.58 2 12.26c0 4.53 2.87 8.37 6.84 9.73.5.1.68-.22.68-.49 0-.24-.01-1.05-.01-1.9-2.78.62-3.37-1.22-3.37-1.22-.45-1.19-1.11-1.5-1.11-1.5-.91-.64.07-.63.07-.63 1 .07 1.53 1.06 1.53 1.06.9 1.57 2.36 1.12 2.93.85.09-.67.35-1.12.64-1.38-2.22-.26-4.56-1.14-4.56-5.07 0-1.12.39-2.03 1.03-2.75-.1-.26-.45-1.3.1-2.71 0 0 .84-.28 2.75 1.05A9.38 9.38 0 0 1 12 6.96c.85 0 1.7.12 2.5.34 1.91-1.33 2.75-1.05 2.75-1.05.55 1.41.2 2.45.1 2.71.64.72 1.03 1.63 1.03 2.75 0 3.94-2.34 4.81-4.57 5.07.36.32.68.94.68 1.9 0 1.37-.01 2.47-.01 2.82 0 .27.18.59.69.49A10.08 10.08 0 0 0 22 12.26C22 6.58 17.52 2 12 2Z" />
              </svg>
              <component
                :is="item.icon"
                v-else
                class="text-muted-foreground h-4 w-4 transition-colors group-hover:text-white"
              />
            </div>

            <div>
              <p class="text-muted-foreground font-mono text-[10px]">
                {{ item.label }}
              </p>
              <a
                v-if="item.href"
                :href="item.href"
                :target="item.href.startsWith('http') ? '_blank' : undefined"
                rel="noopener noreferrer"
                class="font-body text-sm font-medium transition-colors hover:text-blue-600"
              >
                {{ item.value }}
              </a>
              <p v-else class="font-body text-sm font-medium">
                {{ item.value }}
              </p>
            </div>
          </div>

          <div class="mt-8 rounded-xl border border-blue-100 bg-blue-50 p-5">
            <div class="mb-2 flex items-center gap-2">
              <div class="h-2 w-2 animate-pulse rounded-full bg-green-500" />
              <span class="font-mono text-[10px] font-medium text-green-600">
                DISPONIBLE PARA PROYECTOS
              </span>
            </div>
            <p class="font-body text-muted-foreground text-sm">
              Actualmente busco oportunidades como Desarrollador Junior. Respondo en menos de 24h.
            </p>
          </div>
        </motion.div>

        <motion.div
          :initial="{ opacity: 0, x: 20 }"
          :while-in-view="{ opacity: 1, x: 0 }"
          :viewport="{ once: true }"
        >
          <div
            v-if="sent"
            class="flex flex-col items-center justify-center py-16 text-center"
          >
            <div class="mb-5 flex h-16 w-16 items-center justify-center rounded-full bg-blue-50">
              <CheckCircle2 class="h-8 w-8 text-blue-600" />
            </div>
            <h3 class="font-heading mb-2 text-xl font-bold">
              ¡Mensaje enviado!
            </h3>
            <p class="font-body text-muted-foreground text-sm">
              Te respondo pronto. ¡Gracias!
            </p>
          </div>

          <form v-else class="space-y-5" @submit.prevent="handleSubmit">
            <div
              v-for="field in fields"
              :key="field.key"
            >
              <label class="text-muted-foreground mb-2 block font-mono text-[10px] tracking-widest">
                {{ field.label.toUpperCase() }}
              </label>
              <input
                :type="field.type"
                :value="form[field.key]"
                :required="field.required"
                class="font-body border-border w-full rounded-xl border bg-white px-4 py-3 text-sm outline-none transition-all focus:border-blue-500 focus:ring-2 focus:ring-blue-100"
                @input="set(field.key, $event.target.value)"
              >
            </div>

            <div>
              <label class="text-muted-foreground mb-2 block font-mono text-[10px] tracking-widest">
                MENSAJE
              </label>
              <textarea
                v-model="form.message"
                required
                rows="4"
                class="font-body border-border w-full resize-none rounded-xl border bg-white px-4 py-3 text-sm outline-none transition-all focus:border-blue-500 focus:ring-2 focus:ring-blue-100"
                placeholder="Cuéntame sobre tu proyecto..."
              />
            </div>

            <button
              type="submit"
              :disabled="sending"
              class="font-body flex w-full items-center justify-center gap-2 rounded-xl bg-blue-600 py-4 text-sm font-medium text-white transition-all hover:bg-blue-700 hover:shadow-lg hover:shadow-blue-200 disabled:opacity-60"
            >
              <div
                v-if="sending"
                class="h-4 w-4 animate-spin rounded-full border-2 border-white/30 border-t-white"
              />
              <template v-else>
                <Send class="h-4 w-4" />
                Enviar mensaje
              </template>
            </button>
          </form>
        </motion.div>
      </div>
    </div>
  </section>
</template>
