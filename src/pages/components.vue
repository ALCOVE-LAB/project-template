<template>
  <div
    class="mx-auto flex-col gap-2 max-w-full w-full min-h-200vh"
    :style="{
      background: `url(https://plus.unsplash.com/premium_photo-1729851529049-09abc2b27fa0?q=80&w=4140&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D) center/cover no-repeat`,
    }"
  >
    <span>1</span>
    <span>1</span>
    <Button
      class="w-fit"
      @click="
        toast({
          title: 'A Toast',
          content: 'This is a toast' + count++,
          duration: 3000,
        })
      "
    >
      A Toast For 3s
    </Button>
    <hr />
    <Button
      class="w-fit"
      @click="
        toast({
          content: 'This is a default' + count++,
          type: 'default',
          closeIcon: true,
        })
      "
    >
      A Toast For Eternity Default
    </Button>

    <Button
      class="w-fit"
      @click="
        toast({
          title: 'A Toast FOR ETERNITY',
          content: 'This is a info' + count++,
          type: 'info',
        })
      "
    >
      A Toast For Eternity Info
    </Button>
    <Button
      class="w-fit"
      @click="
        toast({
          title: 'A Toast FOR ETERNITY',
          content: 'This is a warning' + count++,
          type: 'warning',
        })
      "
    >
      A Toast For Eternity warning
    </Button>
    <Button
      class="w-fit"
      @click="
        toast({
          content: 'This is a success' + count++,
          type: 'success',
        })
      "
    >
      A Toast For Eternity success
    </Button>
    <Button
      class="w-fit"
      @click="
        toast({
          title: 'A Toast FOR ETERNITY',
          content: 'This is a error' + count++,
          type: 'error',
        })
      "
    >
      A Toast For Eternity error
    </Button>
    <Button
      class="w-fit"
      @click="
        toast({
          title: 'A Toast FOR ETERNITY',
          content: 'This is a warning' + count++,
          type: 'warning',
        })
      "
    >
      A Toast For Eternity warning
    </Button>
    <hr />
    <Button
      class="w-fit"
      @click="
        toast({
          title: 'A Toast FOR ETERNITY',
          content: 'This is a toast' + count++,
          type: 'info',
          action: actionButton,
        })
      "
    >
      A Toast With Action
    </Button>
    <Button
      class="w-fit"
      @click="
        toast({
          title: 'A Toast FOR ETERNITY close',
          content: 'This is a toast' + count++,
          type: 'info',
          action: actionButton,
          actionClose: true,
        })
      "
    >
      A Toast With Action Close
    </Button>

    <Button class="w-fit" @click="waitForClose">A Toast And close</Button>
  </div>
</template>

<script lang="ts" setup>
  import { removeToast, toast } from '@/components/Toast';
  import Button from '@/lib/Button.vue';

  const count = ref(0);
  const actionButton = h(
    Button,
    {
      class: 'text-sm !w-fit',
      size: 'sm',
      onClick: () => {
        window.open('https://google.com', '_blank');
      },
    },
    () => '123',
  );

  const waitForClose = () => {
    const id = toast({
      title: 'A Toast wait for close',
      content: 'This is a toast',
    });
    setTimeout(() => {
      removeToast(id);
    }, 3000);
  };
</script>

<style lang="less" scoped></style>

