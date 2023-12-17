<template>
  index
  <router-link :to="{ name: 'Home' }">Home</router-link>
  {{ useRouter().currentRoute.value.meta.bgColor }}
</template>

<script lang="ts" setup>
  import { useRouter } from 'vue-router';
</script>

<route lang="yaml">
meta:
  layout: default
  bgColor: yellow
</route>

