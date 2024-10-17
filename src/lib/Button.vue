<template>
  <button
    class="btn"
    :class="{
      'btn-secondary': secondary,
      'btn-inverted': inverted,
      'btn-info': info,
      'btn-warning': warning,
      'btn-success': success,
      'btn-error': error,

      'btn-outline': outline,
      'btn-round': rounded,

      'btn-xs': size === 'xs',
      'btn-sm': size === 'sm',
      'btn-lg': size === 'lg',

      'btn-loading': loading,
      'btn-disabled': disabled,
    }"
    @click="
      (evt:any) => {
        if (loading || disabled) {
          evt.preventDefault();
          evt.stopPropagation();
        }else{
          emits('click', evt);
        }
      }
    "
  >
    <div
      class="w-full h-full bg-gray/20 absolute z-1 top-0 left-0 flex-center pointer-event-none opacity-0 transition-all duration-400"
      :class="{
        'opacity-100': loading,
      }"
      v-if="loading"
    >
      <LoaderCircle :size="24" class="animate-spin" color="white" />
    </div>
    <div
      class="flex-center gap-2 transition-all"
      :class="{
        'opacity-0': loading,
        '!flex-col-center py-3': iconVertical,
      }"
    >
      <component :is="prefixIcon" :size="prefixIconSize" v-if="prefixIcon"></component>
      <slot></slot>
      <component :is="suffixIcon" :size="suffixIconSize" v-if="suffixIcon"></component>
    </div>
  </button>
</template>

<script lang="ts" setup>
  import { LoaderCircle } from 'lucide-vue-next';
  import { FunctionalComponent } from 'vue';

  withDefaults(
    defineProps<{
      prefixIcon?: FunctionalComponent;
      prefixIconSize?: number;
      suffixIcon?: FunctionalComponent;
      suffixIconSize?: number;
      secondary?: boolean;
      inverted?: boolean;
      outline?: boolean;

      info?: boolean;
      warning?: boolean;
      success?: boolean;
      error?: boolean;
      rounded?: boolean;

      loading?: boolean;
      disabled?: boolean;
      size?: 'xs' | 'sm' | 'md' | 'lg';
      iconVertical?: boolean;
    }>(),
    {
      size: 'md',
      iconVertical: false,
      prefixIconSize: 18,
      suffixIconSize: 18,
    },
  );
  const emits = defineEmits(['click']);
</script>

<style lang="less" scoped>
  .btn-outline-base {
    @apply bg-transparent;
    border-color: currentColor;
  }

  .btn {
    @apply cursor-pointer bg-primary hover:opacity-90 transition-all;
    @apply rounded-2 text-white font-semibold relative;
    @apply overflow-hidden border-1 border-solid border-transparent;
    @apply px-4 text-base min-h-10;
    @apply active:scale-95;

    &.btn-outline {
      @apply text-primary;
      .btn-outline-base;
    }
  }

  .btn-secondary {
    @apply bg-secondary border-transparent;

    &.btn-outline {
      @apply text-secondary;
      .btn-outline-base;
    }
  }

  .btn-inverted {
    @apply bg-inverted border-transparent;

    &.btn-outline {
      .btn-outline-base;
      @apply text-inverted;
    }
  }

  // status
  .btn-warning {
    @apply bg-warning border-transparent;

    &.btn-outline {
      .btn-outline-base;
      @apply text-warning;
    }
  }

  .btn-info {
    @apply bg-info border-transparent;

    &.btn-outline {
      .btn-outline-base;
      @apply text-info;
    }
  }

  .btn-success {
    @apply bg-success border-transparent;

    &.btn-outline {
      .btn-outline-base;
      @apply text-success;
    }
  }

  .btn-error {
    @apply bg-error border-transparent;

    &.btn-outline {
      .btn-outline-base;
      @apply text-error;
    }
  }

  // size
  .btn-xs {
    @apply px-2 text-xs min-h-6;
  }

  .btn-sm {
    @apply px-3 text-sm min-h-8;
  }

  .btn-lg {
    @apply px-6 text-lg min-h-12;
  }

  .btn,
  .btn-lg,
  .btn-sm,
  .btn-xs {
    @apply !leading-[1];
  }

  .btn-round {
    @apply rounded-full aspect-1 p-0;
  }

  .btn-loading {
    @apply cursor-wait;
    @apply active:scale-100;
  }

  .btn-disabled {
    @apply grayscale cursor-not-allowed;
    @apply active:scale-100;
  }
</style>

