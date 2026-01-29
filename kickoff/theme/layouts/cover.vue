<script setup lang="ts">
import { computed } from 'vue';
import { handleBackground } from '../layoutHelper';

const props = defineProps({
  background: {
    default: '',
  },
  dim: {
    type: Boolean,
    default: false,
  },
})

const style = computed(() => handleBackground(props.background, props.dim))
</script>

<template>
  <div class="slidev-layout cover" :style="style">
    <div class="my-auto w-full">
      <slot />
    </div>
  </div>
</template>