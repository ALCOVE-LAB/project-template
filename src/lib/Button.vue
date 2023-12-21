<template>
  <div
    class="v-btn"
    :disabled="loading || disabled"
    :class="{
      loading,
      frame,
    }"
  >
    <font-awesome-icon
      icon="fa-solid fa-spinner"
      class="animate-spin"
      v-if="loading"
    ></font-awesome-icon>
    <slot></slot>
  </div>
</template>

<script lang="ts" setup>
  defineProps({
    disabled: Boolean,
    loading: Boolean,
    frame: Boolean,
  });
</script>

<style lang="less" scoped>
  .v-btn {
    @apply flex items-center justify-center gap-4;
    @apply w-fit text-black cursor-pointer;
    @apply p-4 py-2 transition-all;
    @apply bg-white rounded-2;
    font-size: initial;

    box-shadow: 4px 4px 0 0 var(--primary);

    &.frame {
      box-shadow: 4px 4px 0 0 var(--secondary);

      &:hover {
        @apply bg-secondary text-white;
        box-shadow: 0 0;
      }
    }

    &:hover {
      @apply bg-primary text-white;
      box-shadow: 0 0;
    }

    &:active {
      box-shadow: 0 0;
      transform: translate(4px, 4px);
    }

    &.loading {
      @apply cursor-not-allowed;
      box-shadow: 0 0;
      filter: contrast(0.5);
    }
  }
</style>

