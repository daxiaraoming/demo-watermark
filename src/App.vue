<script setup>
import { ref } from 'vue';
import { Watermark } from '@pansy/vue-watermark';

const watermark = ref({
  visible: true,
  options: {
    text: 'test',
  }
})

const visible = ref(false)

const showModal = () => {
  watermark.value.options.monitor = false;
  visible.value = true;
};
const showModal2 = () => {
  if (!watermark.value.options.monitor) {
    //加上下面这句弹框一次后也会无响应
    // watermark.value.options.monitor = true;
  }
  visible.value = true;
};
</script>

<template>
  <Watermark :options="watermark.options" :visible="watermark.visible" :is-body="true"> </Watermark>
  <div>
    <a-button @click="showModal">不会卡</a-button>
    <a-button @click="showModal2">会卡</a-button>
    <a-modal v-model:visible="visible" title="Basic Modal">
      <p>Some contents...</p>
    </a-modal>
  </div>
</template>
