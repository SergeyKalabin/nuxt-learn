<template>
  <component
    :is="tag"
    :class="['button', variant, { disabled }]"
    :disabled="tag === 'button' ? disabled : undefined"
    :href="tag === 'a' ? href : undefined"
    :target="href && target ? '_blank' : undefined"
    role="button"
    :style="props.customStyles"
  >
    <slot />
  </component>
</template>

<script setup lang="ts">

const props = withDefaults(
  defineProps<{
    variant?: 'primary' | 'ghost';
    tag?: 'div' | 'button' | 'a';
    href?: string;
    target?: boolean;
    disabled?: boolean;
    customStyles?: Record<string, string> | null;
    label?: string | null;
  }>(),
  {
    variant: 'primary',
    tag: 'div',
    href: '',
    target: false,
    disabled: false,
    customStyles: null,
    label: null,
  }
);
</script>

<style scoped lang="scss">
.button {
  border-radius: 4px;
  border: 1px solid var(--color-black);
  cursor: pointer;
  padding: 16px;
  font-size: 16px;
  font-weight: 700;
}
.primary {
  background: var(--color-black);
  font-family: var(--font);
  color: var(--color-white-light);
}

.primary:hover {
  background-color: var(--color-black-hover);
}

.ghost {
  background: var(--color-white-light);
  font-family: var(--font);
  color: var(--color-black);
}

.ghost:hover {
  background-color: var(--color-black-hover);
  color: var(--color-white-light);
}
</style>
