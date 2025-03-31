<script setup lang="ts">
import { Tooltip } from 'reka-ui/namespaced';
</script>

<template>
  <div class="flex justify-center items-center h-screen">
    <Tooltip.Provider :delay-duration="0">
      <Tooltip.Root>
        <Tooltip.Trigger>
          <div class="bg-pink-100 min-h-10 max-h-96 w-96" />
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