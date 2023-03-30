<template>
  <li>
    <base-card>
      <a :href="url" target="_blank" rel="noopener noreferrer">
        <h3>{{ title }}</h3>
      </a>
      <base-button mode="flat" @click="removeResource(id)"
        >Delete item</base-button
      >
      <p>{{ description }}</p>
    </base-card>
  </li>
</template>

<script setup>
import { inject } from 'vue';

const props = defineProps({
  id: String,
  url: String,
  title: String,
  description: String,
});

const removeResource = inject('removeResource');
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>
