<template>
  <div class="sticky top-0 left-0 bg-white/30 shadow-sm backdrop-blur py-10 px-4 z-10">
    <div class="flex mx-auto w-ful max-w-1440px">
      <router-link to="/components">Components</router-link>
    </div>
  </div>
  <div class="flex-col items-center gap-10 pb-20">
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

    <Card class="mx-10 max-w-1440px leading-tight">{{ str.repeat(20) }}</Card>
    <Card class="mx-10 max-w-1440px leading-snug">{{ str.repeat(20) }}</Card>
    <Card class="mx-10 max-w-1440px text-lg-relaxed">
      <template #title>
        <h2 class="leading-loose text-3xl font-bold">What a wonderful world</h2>
      </template>
      {{ str.repeat(20) }}
      <template #bottom>
        <div class="flex-col gap-4 flex-wrap">
          <div class="flex gap-4 items-center">
            <Button size="xs">Button</Button>
            <Button size="sm">Button</Button>
            <Button>Button</Button>
            <Button size="lg">Button</Button>
          </div>
          <div class="flex gap-4 items-center">
            <Button outline size="sm">Button</Button>
            <Button outline secondary size="sm">Button</Button>
            <Button outline inverted size="sm">Button</Button>
          </div>
          <div class="flex gap-4 items-center">
            <Button outline info size="sm">Button</Button>
            <Button outline error size="sm">Button</Button>
            <Button outline success size="sm">Button</Button>
            <Button outline warning size="sm">Button</Button>
          </div>
          <div class="flex gap-4 items-center">
            <Button info size="sm">Button</Button>
            <Button error size="sm">Button</Button>
            <Button success size="sm">Button</Button>
            <Button warning size="sm">Button</Button>
          </div>
          <div class="flex gap-4 items-center">
            <Button disabled>Button</Button>
            <Button loading>Button</Button>
            <Button :prefixIcon="ArrowRight" :suffixIcon="ArrowLeft" :suffixIconSize="60">
              Button
            </Button>
            <Button rounded :prefixIcon="ArrowRight"></Button>
            <Button rounded>Go</Button>
            <Button rounded loading>Go</Button>
          </div>
        </div>
      </template>
    </Card>
    <Card class="mx-10 max-w-1440px text-xl-loose">{{ str.repeat(20) }}</Card>
    <Card class="mx-10 max-w-1440px leading-loose">{{ str.repeat(20) }}</Card>
  </div>
</template>

<script lang="ts" setup>
  import Button from '@/lib/Button.vue';
  import Card from '@/lib/Card.vue';
  import { ArrowLeft, ArrowRight, Plane } from 'lucide-vue-next';

  const str = 'The quick brown fox jumps over the lazy dog';
  const text = `1234567890 ${str} == ==> <==`;
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

