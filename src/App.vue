<script setup>
import { ref } from 'vue'
import { RouterView } from 'vue-router'
import BackIcon from '@/components/icons/BackIcon.vue'
import BottomNav from './components/BottomNav.vue'

const showDisclaimer = ref(true)

import '@fontsource/dm-sans/100.css'
import '@fontsource/dm-sans/200.css'
import '@fontsource/dm-sans/300.css'
import '@fontsource/dm-sans/400.css'
import '@fontsource/dm-sans/500.css'
import '@fontsource/dm-sans/600.css'
import '@fontsource/dm-sans/700.css'
import '@fontsource/dm-sans/800.css'
import '@fontsource/dm-sans/900.css'
</script>

<template>
  <header
    class="h-14 p-4 w-full absolute"
    :class="
      $route.meta.absolute
        ? 'bg-linear-to-b dark:from-black to-transparent bg-transparent'
        : 'bg-transparent'
    "
  >
    <back-icon
      v-if="$route.meta.showBack"
      class="cursor-pointer size-6"
      @click="$router.back()"
    ></back-icon>
    <div v-else>
      <h1 class="font-semibold text-xl">
        Dígalo con Mimic<span
          class="bg-linear-to-bl from-violet-500 to-fuchsia-500 bg-clip-text text-transparent font-black text-2xl"
          >AI</span
        >
      </h1>
    </div>
    <transition name="fade">
      <div
        v-if="showDisclaimer"
        class="fixed inset-0 z-50 bg-black/80 flex items-center justify-center px-4"
      >
        <div class="bg-purple-200 text-purple-900 w-full rounded-lg p-4 font-bold mb-4">
          <p>Recuerda que las mímicas deben ser lo menos literales posible 🎭❌📣</p>
          <p>Nada de señalar el cielo si es Interestelar 🌌👆 y cosas por el estilo.</p>
          <div class="flex flex-col items-center">
            <button
              class="mt-4 w-full flex items-center justify-center gap-2 px-4 py-2 rounded-lg bg-pink-300 text-white font-medium"
              @click="showDisclaimer = !showDisclaimer"
            >
              ¡Entendido! ☺️
            </button>
            <button
              class="mt-4 w-full flex items-center justify-center gap-2 px-4 py-2 rounded-lg bg-red-400 text-white font-medium"
              @click="showDisclaimer = !showDisclaimer"
            >
              Entendido, pero en rojo 😡
            </button>
          </div>
        </div>
      </div>
    </transition>
  </header>
  <RouterView />
  <BottomNav />
</template>

<style scoped>
@media (min-width: 1024px) {
}
</style>
