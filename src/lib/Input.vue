<template>
  <div class="v-input">
    <!-- suffix -->
    <div class="prefix" v-if="prefix">
      <slot name="prefix"></slot>
    </div>
    <input v-bind="$attrs" :type="type" v-model="currentValue" @blur="inputHanlder" />
    <!-- suffix -->
    <div class="suffix" v-if="suffix">
      <slot name="suffix"></slot>
    </div>
  </div>
</template>

<script lang="ts" setup>
  import BigNumber from 'bignumber.js';
  BigNumber.config({ EXPONENTIAL_AT: 10 });
  const props = defineProps(['modelValue', 'prefix', 'suffix', 'precision', 'type', 'min', 'max']);
  const emits = defineEmits(['update:modelValue']);
  const currentValue = ref('');

  const inputHanlder = (evt: any) => {
    let value = evt.target.value;

    if (props.type == 'number') {
      if (!value || isNaN(value)) {
        value = '';
      }

      if (!isNaN(props.precision)) {
        value = new BigNumber(new BigNumber(value).shiftedBy(props.precision).toFixed(0))
          .shiftedBy(-props.precision)
          .toString();
      }

      if (props.min && BigNumber(value).isLessThan(props.min)) {
        value = props.min;
      }

      if (props.max && BigNumber(value).isGreaterThan(props.max)) {
        value = props.max;
      }
    }
    currentValue.value = value;
    emits('update:modelValue', value);
  };

  watch(
    () => props.modelValue,
    () => {
      currentValue.value = props.modelValue;
    },
    {
      immediate: true,
    },
  );
</script>

<style lang="less" scoped>
  .v-input {
    @apply rounded-3 transition-all flex items-center overflow-hidden;
    @apply bg-accent/10 border-transparent border-2 p-2 px-3;

    &:focus-within {
      @apply border-accent;
    }
  }

  input {
    @apply bg-transparent w-full;
  }

  .prefix,
  .suffix {
    @apply h-full px-1;
  }

  .suffix {
    @apply ml-auto;
  }

  /* Chrome, Safari, Edge, Opera */
  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  /* Firefox */
  input[type='number'] {
    -moz-appearance: textfield;
  }
</style>

