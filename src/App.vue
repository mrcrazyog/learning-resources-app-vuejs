<template>
  <MainHeader title="Remember me" />
  <TheResources />
</template>

<script setup></script>

<script>
import { defineComponent } from 'vue';
import MainHeader from './components/layouts/MainHeader.vue';
import TheResources from './components/resources/TheResources.vue';
export default defineComponent({
  components: {
    MainHeader,
    TheResources,
  },
});
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
:root {
  --card-background-light: #ffffff;
  --card-background-dark: #1f1f1f;
  --text-color-light: #000000;
  --text-color-dark: #ffffff;
  --box-shadow-light: rgba(0, 0, 0, 0.26);
  --box-shadow-dark: rgba(255, 255, 255, 0.15);
}

@media (prefers-color-scheme: light) {
  .card {
    background-color: var(--card-background-light);
    color: var(--text-color-light);
    box-shadow: 0 2px 8px var(--box-shadow-light);
  }
}

@media (prefers-color-scheme: dark) {
  .card {
    background-color: var(--card-background-dark);
    color: var(--text-color-dark);
    box-shadow: 0 2px 8px var(--box-shadow-dark);
  }
}
* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>
