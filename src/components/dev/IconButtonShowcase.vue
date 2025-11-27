<script setup lang="ts">
import IconButton from '../atoms/IconButton.vue';
import { Info, Play, Star } from 'lucide-vue-next';
</script>



<template>
<section>
   <IconButton :icon="Play" variant="primary" size="lg" label="Play Trailer"/>
   <IconButton :icon="Star" variant="secondary" size="md" sr-label="add to watchlist"/>
   <IconButton :icon="Info" variant="ghost" size="sm"  sr-label="show series information"/>
</section>
</template>
