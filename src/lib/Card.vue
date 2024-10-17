<template>
  <div class="rounded-md @light:bg-black/4 @dark:bg-white/4 flex-col shadow-md p-4" v-bind="$attrs">
    <slot name="title"></slot>
    <slot></slot>
    <slot name="bottom"></slot>
  </div>
</template>

<script lang="ts" setup></script>

<style lang="less" scoped></style>

