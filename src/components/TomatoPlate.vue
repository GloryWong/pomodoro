<template>
  <div
    class="tomato-plate w-1/2 h-1/5 flex justify-center items-center"
    v-show="springQueueRunning"
  >
    <div class="w-full" v-for="n in CYCLE_NUMBER" :key="n">
      <img
        class="w-full h-auto select-none"
        :class="
          n === allTomatoSize + 1 && isActiveTomatoSpring()
            ? 'animate-pulse'
            : n > allTomatoSize
            ? 'opacity-50'
            : ''
        "
        src="../assets/tomato.svg"
        loading="lazy"
        alt="tomato"
      />
    </div>
  </div>
</template>

<script lang="ts" setup>
  import { inject } from 'vue'
  import { Tomato } from '../composables'

  const tomato = inject('tomato') as Tomato
  const { CYCLE_NUMBER } = tomato.config
  const { springQueue, springQueueRunning, isActiveTomatoSpring } = tomato
  const allTomatoSize = springQueue.allTomatoSize
</script>
