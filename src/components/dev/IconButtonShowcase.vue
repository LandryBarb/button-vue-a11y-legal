<script setup lang="ts">
import IconButton from '../atoms/IconButton.vue';
import { Info, Play, Star } from 'lucide-vue-next';
</script>



<template>
<section>
   <IconButton :icon="Play" variant="primary" size="lg" label="Play Trailer"/>
   <IconButton :icon="Star" variant="secondary" size="md" srlabel="add to watchlist"/>
   <IconButton :icon="Info" variant="ghost" size="sm"  srlabel="show series information"/>
</section>

<section>
   <IconButton :icon="Star" srLabel="Remove from watchlist"  :pressed="true"/>
   <IconButton :icon="Star" srLabel="Add to watchlist" :pressed="false"/>
</section>
</template>
