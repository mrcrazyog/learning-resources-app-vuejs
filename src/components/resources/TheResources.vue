<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storeResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab" />
  </keep-alive>
</template>

<script setup>
import { ref, provide, computed, reactive } from 'vue';
const props = defineProps({
  id: Number,
  url: String,
  title: String,
  description: String,
});
const selectedTab = ref('stored-resources');
const setSelectedTab = (tab) => {
  selectedTab.value = tab;
};

const addResource = (title, description, url) => {
  const newResource = {
    id: Math.random().toString(36),
    title: title,
    description: description,
    url: url,
  };
  console.log('the new resource is', newResource);
  storedResources.unshift(newResource);
  selectedTab.value = 'stored-resources';
};

const removeResource = (id) => {
  const resourceIndex = storedResources.findIndex((res) => res.id === id);
  if (resourceIndex >= 0) {
    storedResources.splice(resourceIndex, 1);
  }
};

const storedResources = reactive([
  {
    id: '1',
    title: 'Vue 3',
    description:
      'Vue 3 is a major update to Vue.js, the progressive framework for building user interfaces.',
    url: 'https://v3.vuejs.org/',
  },
  {
    id: '2',
    title: 'Vite',
    description:
      'Vite is a new breed of frontend build tool that significantly improves the frontend development experience.',
    url: 'https://vitejs.dev/',
  },
  {
    id: '3',
    title: 'Volar',
    description:
      'Volar is a Vue language support extension for VS Code, powered by @vue/reactivity and @vue/compiler-sfc.',
    url: 'https://google.com/',
  },
]);

provide('storedResources', storedResources);
provide('addResource', addResource);
provide('removeResource', removeResource);

const storeResButtonMode = computed(() => {
  return selectedTab.value === 'stored-resources' ? null : 'flat';
});

const addResButtonMode = computed(() => {
  return selectedTab.value === 'add-resource' ? null : 'flat';
});
</script>

<script>
import { defineComponent } from 'vue';
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
export default defineComponent({
  components: {
    StoredResources,
    AddResource,
  },
});
</script>
