<template>
  <div class="rounded-md bg-black/4 flex-col shadow-md p-4" v-bind="$attrs">
    <slot name="title"></slot>
    <slot></slot>
    <slot name="bottom"></slot>
  </div>
</template>

<script lang="ts" setup></script>

<style lang="less" scoped></style>

