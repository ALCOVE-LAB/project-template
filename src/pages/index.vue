<template>
  <Container class="flex-col items-center gap-2 p-20 py-30">
    <!-- gasp -->
    <!-- animejs -->
    <Slider v-model:modelValue="count" :min="0" :max="100" :step="1" />
    <StatsPanelList />
    <Cards />
    <Typography />
  </Container>
</template>

<script lang="ts" setup>
  import Container from '@/lib/Container.vue';
  import Slider from '@/lib/Slider.vue';

  const count = ref(0);
</script>

<route lang="yaml">
meta:
  layout: default
</route>

