<script setup>
import { Mail } from '@lucide/vue'

const year = new Date().getFullYear()
</script>

<template>
  <footer class="border-border border-t px-6 py-8">
    <div class="mx-auto flex max-w-5xl flex-col items-center justify-between gap-4 sm:flex-row">
      <p class="text-muted-foreground font-mono text-xs">
        © {{ year }} Pedro Barra Pino — Temuco, Chile
      </p>

      <div class="flex items-center gap-4">
        <a
          href="https://github.com/iabdielll"
          target="_blank"
          rel="noopener noreferrer"
          class="text-muted-foreground hover:text-foreground transition-colors"
          aria-label="GitHub"
        >
          <svg
            class="h-4 w-4"
            viewBox="0 0 24 24"
            fill="currentColor"
            aria-hidden="true"
          >
            <path d="M12 2C6.48 2 2 6.58 2 12.26c0 4.53 2.87 8.37 6.84 9.73.5.1.68-.22.68-.49 0-.24-.01-1.05-.01-1.9-2.78.62-3.37-1.22-3.37-1.22-.45-1.19-1.11-1.5-1.11-1.5-.91-.64.07-.63.07-.63 1 .07 1.53 1.06 1.53 1.06.9 1.57 2.36 1.12 2.93.85.09-.67.35-1.12.64-1.38-2.22-.26-4.56-1.14-4.56-5.07 0-1.12.39-2.03 1.03-2.75-.1-.26-.45-1.3.1-2.71 0 0 .84-.28 2.75 1.05A9.38 9.38 0 0 1 12 6.96c.85 0 1.7.12 2.5.34 1.91-1.33 2.75-1.05 2.75-1.05.55 1.41.2 2.45.1 2.71.64.72 1.03 1.63 1.03 2.75 0 3.94-2.34 4.81-4.57 5.07.36.32.68.94.68 1.9 0 1.37-.01 2.47-.01 2.82 0 .27.18.59.69.49A10.08 10.08 0 0 0 22 12.26C22 6.58 17.52 2 12 2Z" />
          </svg>
        </a>

        <a
          href="mailto:abdielbarrapino@gmail.com"
          class="text-muted-foreground transition-colors hover:text-blue-600"
          aria-label="Email"
        >
          <Mail class="h-4 w-4" />
        </a>
      </div>
    </div>
  </footer>
</template>
