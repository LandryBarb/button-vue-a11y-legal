<script setup lang="ts">
import IconButton from '../atoms/IconButton.vue';
import { Info, Play, Star } from 'lucide-vue-next';
</script>



<template>
<section>
   <IconButton :icon="Play" variant="primary" size="lg" />
   <IconButton :icon="Star" variant="secondary" size="md" :loading="false"/>
   <IconButton :icon="Info" variant="ghost" size="sm" label="info"/>
</section>
</template>
