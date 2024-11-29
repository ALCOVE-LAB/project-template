<template>
  <div class="grid gap-3 grid-cols-[minmax(400px,1fr)_auto] w-full">
    <div class="w-full bg-black/4">
      <router-view></router-view>
    </div>
    <div class="w-66 bg-black/4"></div>
  </div>
</template>

<script lang="ts" setup></script>

<style lang="less" scoped></style>

<route lang="yaml">
meta:
  layout: side
</route>

