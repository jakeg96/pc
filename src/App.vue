<script setup lang="ts">
import { Icon } from '@iconify/vue'
</script>

<template>
  <div>
    <header class="flex items-center bg-zinc-200 text-zinc-700 gap-4 pl-4 pt-1 pb-1 rounded-t-2xl border-b border-zinc-700">
      <Icon icon="streamline-pixel:coding-apps-websites-programming-browser" class="size-4" />
      <button class="text-md font-pixelbold">jakegreen.dev</button>
      <button class="text-md hover:text-zinc-400">File</button>
      <button class="text-md hover:text-zinc-400">Edit</button>
      <button class="text-md hover:text-zinc-400">View</button>
      <button class="text-md hover:text-zinc-400">Help</button>
    </header>
    <body class="flex flex-col justify-center items-center text-zinc-500">
      <div class="flex flex-col fixed top-7/12 left-1/5 items-center justify-center">
        <Icon icon="streamline-pixel:coding-apps-websites-finder" class="text-zinc-300 size-13 pb-1" />
        <p class="bg-zinc-300 px-1 text-zinc-700 text-md font-bold">Finder</p>
      </div>
      <div class="flex flex-col fixed top-5/12 left-3/5 items-center justify-center">
        <Icon icon="streamline-pixel:interface-essential-bin" class="text-zinc-300 size-13 pb-1" />
        <p class="bg-zinc-300 px-1 text-zinc-700 text-md font-bold">WasteBasket</p>
      </div>
    </body>
  </div>
</template>
