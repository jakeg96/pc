<script setup lang="ts">
import { ref } from 'vue'
import { Icon } from '@iconify/vue'
const card = ref<HTMLElement>()
let startX = 10,
  startY = 10

const dragCard = (e: MouseEvent | TouchEvent) => {
  // Prevent default to avoid scrolling on mobile
  e.preventDefault()

  const cardElement = card.value
  if (!cardElement) return

  const rect = cardElement.getBoundingClientRect()

  // Get the correct client coordinates for both mouse and touch events
  const clientX = 'touches' in e ? e.touches[0].clientX : e.clientX
  const clientY = 'touches' in e ? e.touches[0].clientY : e.clientY

  startX = clientX - rect.left
  startY = clientY - rect.top

  const onMove = (event: MouseEvent | TouchEvent) => {
    event.preventDefault()

    // Get coordinates for both mouse and touch events
    const moveClientX = 'touches' in event ? event.touches[0].clientX : event.clientX
    const moveClientY = 'touches' in event ? event.touches[0].clientY : event.clientY

    const x = moveClientX - startX
    const y = moveClientY - startY

    cardElement.style.position = 'fixed'
    cardElement.style.left = `${x}px`
    cardElement.style.top = `${y}px`
    cardElement.style.zIndex = '1000'
  }

  const onEnd = () => {
    // Remove both mouse and touch event listeners
    window.removeEventListener('mousemove', onMove)
    window.removeEventListener('mouseup', onEnd)
    window.removeEventListener('touchmove', onMove)
    window.removeEventListener('touchend', onEnd)
  }

  // Add both mouse and touch event listeners
  window.addEventListener('mousemove', onMove, { passive: false })
  window.addEventListener('mouseup', onEnd)
  window.addEventListener('touchmove', onMove, { passive: false })
  window.addEventListener('touchend', onEnd)
}

const emits = defineEmits<{
  terminalOn: [boolean]
}>()
</script>

<template>
  <div class="relative border bg-zinc-400 border-zinc-900 rounded-[6px] z-10 touch-none" ref="card">
    <div
      class="flex items-center border-b border-zinc-900 select-none bg-zinc-300 rounded-t-[6px]"
    >
      <div
        class="px-2 text-zinc-700 active:bg-zinc-600 active:text-white rounded-[4px] cursor-pointer"
        @click="emits('terminalOn', false)" @touch="emits('terminalOn', false)"
      >
        x
      </div>
      <div class="flex items-center justify-center w-full" @mousedown="dragCard" @touchstart="dragCard">
        <div class="rounded-[6px] border-x px-0.5 border-zinc-700">
          <div class="rounded-[6px] border-x-2 px-0.5 border-zinc-700">
            <div class="rounded-[6px] border-x-4 px-0.5 border-zinc-700">
              <div class="text-white bg-zinc-700 px-1 rounded-[6px]">Terminal</div>
            </div>
          </div>
        </div>
      </div>
      <Icon
          icon="streamline-pixel:coding-apps-websites-programming-browser"
          class="size-4 mx-1 text-zinc-900"
        />
    </div>
    <div class="flex flex-col text-zinc-900 px-1">
      <div>jake@jakegreen ~ %</div>
    </div>
  </div>
</template>
