<template>
  <ul>
    <ResourceItem
      v-for="resource in storedResources"
      :key="resource.id"
      :id="resource.id"
      :url="resource.url"
      :title="resource.title"
      :description="resource.description"
    />
  </ul>
</template>

<script setup></script>

<script>
import ResourceItem from './ResourceItem.vue';
export default {
  components: {
    ResourceItem,
  },
  inject: ['storedResources'],
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
