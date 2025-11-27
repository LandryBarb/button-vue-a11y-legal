<script setup lang="ts">
import ButtonShowcase from './components/dev/ButtonShowcase.vue';
import IconButtonShowcase from './components/dev/IconButtonShowcase.vue';


</script>

<template>

<ButtonShowcase />
<IconButtonShowcase />
</template>

<style scoped>
section {
  padding: 2rem;
  display: grid;
  grid-template-columns: repeat(auto, 1fr);
  gap: 1rem;
  
}
</style>
