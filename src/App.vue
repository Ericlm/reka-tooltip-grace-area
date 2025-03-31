<script setup lang="ts">
import { Tooltip } from 'reka-ui/namespaced'
import { onMounted, ref, useTemplateRef } from 'vue';

const div = useTemplateRef('div')

const startHeight = ref(0)
const startY = ref(0)

const newHeight = ref(500)

function resize(event: PointerEvent) {
  if (!div.value) return

  newHeight.value = startHeight.value + event.clientY - startY.value;
}

function initResize(event: PointerEvent) {
  if (!div.value || !document.defaultView) return

  startY.value = event.clientY;
  startHeight.value = parseInt(document.defaultView.getComputedStyle(div.value).height)

  document.addEventListener('pointermove', resize)
  document.addEventListener('pointerup', () => {
    document.removeEventListener('pointermove', resize)
  })
}
</script>

<template>
  <div class="flex justify-center items-center h-screen">
    <Tooltip.Provider :delay-duration="0">
      <Tooltip.Root>
        <Tooltip.Trigger>
          <div class="bg-pink-100 w-96" ref="div" @pointerdown="initResize" :style="{ height: newHeight + 'px' }" />
        </Tooltip.Trigger>

        <Tooltip.Portal>
          <Tooltip.Content class="bg-gray-600 text-white">
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Beatae, quod.
          </Tooltip.Content>
        </Tooltip.Portal>
      </Tooltip.Root>
    </Tooltip.Provider>
  </div>
</template>