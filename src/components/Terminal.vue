<script setup lang="ts">
import { Icon } from '@iconify/vue'
import { ref, defineEmits } from 'vue'

const card = ref(undefined)
let startX = 10,
    startY = 10

const dragCard = (e: any) => {
  const cardElement: any = card.value

  const rect = cardElement?.getBoundingClientRect()
  startX = e.clientX - rect.left
  startY = e.clientY - rect.top

  const onMouseMove = (event: any) => {
    const x = event.clientX - startX
    const y = event.clientY - startY

    cardElement.style.position = 'fixed'
    cardElement.style.left = `${x}px`
    cardElement.style.top = `${y}px`
  }

  const onMouseUp = () => {
    window.removeEventListener('mousemove', onMouseMove)
    window.removeEventListener('mouseup', onMouseUp)
  }

  window.addEventListener('mousemove', onMouseMove)
  window.addEventListener('mouseup', onMouseUp)
}

const emits = defineEmits<{
  terminalOn: [boolean]
}>()
</script>

<template>
  <div
    class="relative border bg-zinc-400 border-zinc-900 rounded-[6px] z-10"
    ref="card"
    @mousedown="dragCard"
  >
    <div
      class="flex justify-between items-center border-b border-zinc-900 select-none bg-zinc-300 rounded-t-[6px]"
    >
      <div
        class="px-2 text-zinc-700 -md active:bg-zinc-600 active:text-white rounded-[4px]"
        @click="emits('terminalOn', false)"
      >
        x
      </div>
      <div class="rounded-[6px] border-x px-0.5 border-zinc-700">
        <div class="rounded-[6px] border-x-2 px-0.5 border-zinc-700">
          <div class="rounded-[6px] border-x-4 px-0.5 border-zinc-700">
            <div class="text-white bg-zinc-700 px-1 rounded-[6px]">Terminal</div>
          </div>
        </div>
      </div>
      <div>
        <Icon
          icon="streamline-pixel:coding-apps-websites-programming-browser"
          class="size-4 mx-1 text-zinc-700"
        />
      </div>
    </div>
    <div class="flex flex-col text-zinc-900 px-1">
      <div>jake@jakegreen ~ %</div>
    </div>
  </div>
</template>
