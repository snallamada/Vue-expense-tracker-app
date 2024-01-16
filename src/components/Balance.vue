<template>
  <center><h2>Your Balance</h2>
  <h1 id="balance">${{ total }}</h1></center>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
