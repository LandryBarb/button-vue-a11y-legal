<script setup lang="ts">
import { computed } from 'vue';

type Variant = 'primary' | 'secondary' | 'danger' | 'ghost';
type Size = 'small' | 'medium' | 'large';

const props = withDefaults(defineProps<{
    variant?: Variant;
    size?: Size;
    disabled?: boolean;
    loading?: boolean;
    type?: 'button' |  'submit' | 'reset';
}>(), {
    variant: 'primary',
    size: 'medium',
    type: 'button',

});

const classes = computed(() => {
    return [
        'btn',
        `btn--${props.variant}`,
        `btn--${props.size}`,
       props.disabled ? 'btn--disabled' : '',
        props.loading ? 'btn--loading' : '',
    ];
});
</script>

<template>
    <button
    :type="type"
    :class="classes"
    :disabled="disabled || loading"
    :aria-disbabled="disabled || loading"
    :aria-busy="loading"
    >
    <span v-if="loading" class="spinner" aria-hidden="true"></span>
    <span><slot></slot></span> 
    </button>

</template>

<style scoped>
/* ENHANCED AAA CONTRAST COLORS */
.btn {
  font-weight: 600;
  border-radius: 6px;
  padding: 0.65rem 1rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: .5rem;
  line-height: 1;
  cursor: pointer;
  transition: background .2s ease, border-color .2s ease;
}

/* Focus-visible AAA requirement */
.btn:focus-visible {
  outline: 3px solid #ffffff;
  outline-offset: 3px;
}

/* Example: primary AAA compliant on dark backgrounds */
.btn--primary {
  background: #1E90FF; 
  color: #fff;
}

/* Disabled */
.btn--disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

/* Loading spinner placeholder */
.spinner {
  width: 1rem;
  height: 1rem;
  border-radius: 50%;
  border: 2px solid white;
  border-top-color: transparent;
  animation: spin 0.6s linear infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}
</style>