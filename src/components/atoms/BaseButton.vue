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
  text-transform: uppercase;
  justify-content: center;
  gap: .5rem;
  line-height: 1;
  cursor: pointer;
  transition: background .2s ease, border-color .2s ease;
}
.btn:hover:not(.btn--disabled):not(.btn--loading) {
  filter: brightness(90%);
}
/* Focus-visible AAA requirement */
.btn:focus-visible {
  outline: 3px solid #ffffff;
  outline-offset: 7px;
}

/* Example: primary AAA compliant on dark backgrounds */
.btn--primary {
  background: #1E90FF; 
  color: #fff;
}
.btn--secondary {
  background: #32CD32; 
  color: #fff;
}
.btn--danger {
  background: #FF4500; 
  color: #fff;
}
.btn--ghost {
  background: transparent; 
  color: #1E90FF; 
  border: 2px solid #1E90FF;
}

.btn--small {
  padding: 0.4rem 0.75rem;
  font-size: 0.875rem;
}
.btn--medium {
  padding: 0.65rem 1rem;
  font-size: 1rem;
}
.btn--large{
    padding: 0.85rem 1.5rem;
    font-size: 1.125rem;
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