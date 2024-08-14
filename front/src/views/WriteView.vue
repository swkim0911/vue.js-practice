<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>
<style></style>
<template>
  <p>안녕하세요</p>
  <button @click="count += 1">버튼을 눌러주세요</button>
  <p>Count: {{ count }}</p>
</template>
