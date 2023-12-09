<template>
  <div class="flex-col">
    <span class="text-red">SomeComp</span>
    <div class="text-blue">Some Comp SubTitle 8888888</div>
    <p>
      {{ new BigNumber(123456).toFormat() }}
    </p>
    <p>
      {{ new BigNumber(123123.456789).toFormat() }}
    </p>
  </div>
</template>

<script lang="ts" setup>
  import BigNumber from 'bignumber.js';
</script>

