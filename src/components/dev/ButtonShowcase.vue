<script setup lang="ts">
import BaseButton from '../atoms/BaseButton.vue';

</script>



<template>
<section>
      <BaseButton variant="secondary" size="large" :loading="false">
    Play Episode
  </BaseButton>
  <BaseButton variant="primary" size="medium" :loading="false">
add to favorites
  </BaseButton>

  <BaseButton variant="ghost" size="small" :loading="false">    
    more info
  </BaseButton>
  <BaseButton variant="danger" size="large" :loading="true" :disabled="true">
    Delete Account
</BaseButton>
</section>
</template>

  