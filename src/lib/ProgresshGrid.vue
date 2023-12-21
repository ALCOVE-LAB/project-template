<template>
  <div class="flex items-center flex-wrap gap-2px">
    <span
      class="min-w-2 h-4 bg-accent/30 transaction-all rounded-2px"
      v-for="n in Number(total)"
      :key="n"
      :class="{
        'flex-1 cursor-default': total <= 115,
        'bg-green/50 cursor-pointer': n < current,
        'bg-green animate-pulse cursor-pointer': n == current,
      }"
      @click="n <= current && $emit('item-click', n - 1)"
    ></span>
  </div>
</template>

<script lang="ts" setup>
  defineProps(['total', 'current']);
</script>

