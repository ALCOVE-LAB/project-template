<template>
  <div class="text-10 py-10 flex-col-axis-center gap-8">
    <span
      class="hidden font-mono font-sans font-serif font-normal font-medium font-semibold font-bold font-extrabold font-black"
    ></span>
    <div :class="`${font}`" class="relative w-fit" v-for="font in fontList" :key="font">
      <span class="absolute left-0 -top-4 text-sm">{{ font }}</span>
      {{ text }}
    </div>
    <Plane />
  </div>
</template>

<script lang="ts" setup>
  import { Plane } from 'lucide-vue-next';

  const text = '1234567890 abcdefghui ABCDEFGHIJKLMNOPQRSTUVWXYZ == ==> <==';
  const font = ['normal', 'medium', 'bold', 'black'];
  const fontFace = ['mono', 'sans'];

  const fontList = fontFace
    .map((face) => {
      return font.map((weight) => {
        return `font-${face} font-${weight}`;
      });
    })
    .flat();
</script>

<route lang="yaml">
meta:
  layout: default
</route>

