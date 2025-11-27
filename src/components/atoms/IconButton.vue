<script setup lang="ts">
import { computed, defineProps, withDefaults } from 'vue';

type Variant = 'primary' | 'secondary' | 'ghost' | 'danger' | 'warning';
type Size = 'sm' | 'md' | 'lg';

const props = withDefaults(
  defineProps<{
   icon?: any; // will be a component
    variant?: Variant;
    size?: Size;
    disabled?: boolean;
    loading?: boolean;
    label?: string; //optional visible label for accessibility
  }>(),
  {
    variant: 'primary',
    size: 'md',
    disabled: false,
    loading: false,
    label: '',
  });

  const classes = computed(() =>  [
      `icon-btn`,
      `icon-btn--${props.variant}`,
      `icon-btn--${props.size}`,
      props.disabled ? 'icon-btn--disabled' : '',
      props.loading ? 'icon-btn--loading' : '',
    ]);
</script>

<template>
  <button
    :class="classes"
    :disabled="disabled || loading"
    type="button"
  >
   <!-- Loading spinner (placeholder) -->
    <span v-if="loading" class="spinner" aria-hidden="true"></span>
    <!-- Icon -->
    <component v-else :is="icon" class="icon-btn__icon" aria-hidden="true" />
    <!-- Accessible label -->
     <span v-if="label" class="icon-btn__label">{{ label }}</span>
  </button>
</template>

<style scoped>
.icon-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: .35rem;
  border-radius: 6px;
  font-weight: 600;
  text-transform: uppercase;
  cursor: pointer;
  padding: .5rem;
  transition: background .2s ease, border-color .2s ease;
}

.icon-btn__icon {
  width: 1.25rem;
  height: 1.25rem;
}

/* Sizes */
.icon-btn--sm { padding: .35rem; }
.icon-btn--md { padding: .5rem; }
.icon-btn--lg { padding: .75rem; }

/* Variants (mirrors BaseButton) */
.icon-btn--primary {
  background: #1E90FF;
  color: white;
}

.icon-btn--secondary {
  background: #333;
  color: white;
}

.icon-btn--ghost {
  background: transparent;
  color: white;
}

.icon-btn--danger {
  background: #D32F2F;
  color: white;
}

/* Loading */
.spinner {
  width: 1rem;
  height: 1rem;
  border-radius: 50%;
  border: 2px solid white;
  border-top-color: transparent;
  animation: spin .6s linear infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}
</style>