<script setup lang="ts">
import { ref } from 'vue'
import { Icon } from '@iconify/vue'
import Terminal from './components/Terminal.vue'

const terminalOn = ref(false)
</script>

<template>
  <div>
    <header
      class="flex items-center bg-zinc-200 text-zinc-700 py-1 rounded-t-2xl border-b border-zinc-700"
    >
      <Icon icon="streamline-pixel:coding-apps-websites-programming-browser" class="size-4 ml-4 mr-2" />
      <div class="flex gap-4">
        <button class="font-pixelbold active:bg-zinc-600 active:text-white rounded-[6px]">
          jakegreen.dev
        </button>
        <button class="active:bg-zinc-600 active:text-white px-1 rounded-[6px]">File</button>
        <button class="active:bg-zinc-600 active:text-white px-1 rounded-[6px]">Edit</button>
        <button class="active:bg-zinc-600 active:text-white px-1 rounded-[6px]">View</button>
        <button class="active:bg-zinc-600 active:text-white px-1 rounded-[6px]">Help</button>
      </div>
    </header>
    <body>
      <div>
        <Terminal v-if="terminalOn" @terminal-on="terminalOn = $event"  class="w-9/12 max-w-130 h-60"/>
      </div>
      <div class="flex flex-col fixed top-7/12 left-3/12 items-center justify-center">
        <Icon
          icon="streamline-pixel:coding-apps-websites-finder"
          class="text-zinc-300 size-13 pb-1"
        />
        <p class="bg-zinc-300 px-1 text-zinc-700">Finder</p>
      </div>
      <div class="flex flex-col fixed top-5/12 left-7/12 items-center justify-center">
        <Icon icon="streamline-pixel:interface-essential-bin" class="text-zinc-300 size-13 pb-1" />
        <p class="bg-zinc-300 px-1 text-zinc-700">WasteBasket</p>
      </div>
      <div
        class="flex flex-col fixed top-8/12 left-6/12 items-center justify-center active:text-zinc-700"
      >
        <Icon
          icon="streamline-pixel:coding-apps-websites-programming-browser"
          class="text-zinc-300 size-13 pb-1 active:text-zinc-700"
          @click="terminalOn = true"
        />
        <p class="bg-zinc-300 px-1 text-zinc-700">Terminal</p>
      </div>
    </body>
  </div>
</template>
