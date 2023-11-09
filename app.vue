
<script setup lang="ts">
const show = ref(false)
</script>

<template>
  <div>
    <BButton variant="primary" @click="show = !show">Click me</BButton>
    <BModal v-model="show">Test</BModal>
  </div>
</template>
