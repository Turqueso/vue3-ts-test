<template>
  <button
    class="btn font-montserrat"
    :class="{ btn__outline: outline, disabled: disabled }"
    :type="type"
    @click="click"
    :disabled="disabled"
  >
    <slot />
  </button>
</template>

<script setup lang="ts">
withDefaults(
  defineProps<{
    outline?: boolean;
    type?: "submit" | "button";
    disabled?: boolean;
  }>(),
  {
    outline: false,
    type: "button",
    disabled: false,
  }
);
const emit = defineEmits<{
  (e: "click"): void;
}>();

function click() {
  emit("click");
}
</script>

<style scoped>
.btn {
  border: 1px solid transparent;
  background: var(--primary);
  color: white;
  border-radius: var(--border-radius);
  padding: 0.5rem 3rem;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.2), 0 1px 4px rgba(0, 0, 0, 0.12),
    0 2px 2px rgba(0, 0, 0, 0.14);
}

.btn.btn__outline {
  background: var(--light);
  border-color: var(--primary);
  color: var(--primary);
}
.btn.disabled {
  opacity: 0.5;
  pointer-events: none;
}
</style>
