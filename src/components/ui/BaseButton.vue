<template>
  <button :type="type" :class="mode">
    <slot></slot>
  </button>
</template>

<script setup>
const props = defineProps({
  type: {
    type: String,
    default: 'button',
  },
  mode: {
    type: String,
  },
});
</script>

<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #3a0061;
  border: 1px solid #3a0061;
  color: white;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: #270041;
  border-color: #270041;
}

.flat {
  background-color: rgb(156, 88, 88);
  color: #3a0061;
  border: 1px solid #3a0061;
}

.flat:hover,
.flat:active {
  background-color: #edd2ff;
}
</style>
