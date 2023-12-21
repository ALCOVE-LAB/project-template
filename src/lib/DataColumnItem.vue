<template>
  <div
    class="flex-col sm:flex-row items-center gap-1 justify-between text-sm sm:text-base hover:bg-primary/10 transition-all px-2 py-2 rounded-2"
  >
    <slot name="title">
      <span class="font-semibold text-text/60 text-sm">{{ title }}</span>
    </slot>
    <slot name="value">
      <span class="break-all text-base" :class="valueClass">{{ value }}</span>
    </slot>
  </div>
</template>

<script lang="ts" setup>
  defineProps(['title', 'value', 'valueClass']);
</script>

