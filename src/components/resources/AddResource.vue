<template>
  <h2>Add resource</h2>
  <base-dialog
    v-if="inputIsInvalid"
    title="Invalid input entered, please correct"
    @onDivClick="confirmError"
  >
    <template #content>
      <p>
        Please enter a valid title, description, and URL. The URL should start
        with "http://" or "https://".
      </p>
    </template>
    <template #actions>
      <base-button mode="outline" @click="confirmError"> Okay </base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="handleSubmit">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" id="title" ref="titleRef" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea id="description" rows="5" ref="descriptionRef"></textarea>
      </div>
      <div class="form-control">
        <label for="url">URL</label>
        <input type="url" id="url" ref="urlRef" />
      </div>
      <div class="actions">
        <base-button mode="outline" @click="resetForm">Reset</base-button>
        <base-button mode="success" type="submit">Add resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script setup>
import { ref, inject } from 'vue';

const titleRef = ref(null);
const descriptionRef = ref(null);
const urlRef = ref(null);
const inputIsInvalid = ref(false);

const handleSubmit = () => {
  const submitData = {
    title: titleRef.value.value,
    description: descriptionRef.value.value,
    url: urlRef.value.value,
  };
  if (
    submitData.title.trim().length === 0 ||
    submitData.description.trim().length === 0 ||
    submitData.url.trim().length === 0
  ) {
    inputIsInvalid.value = true;

    return;
  }
  addResource(submitData.title, submitData.description, submitData.url);
  console.log(submitData);
};

const addResource = inject('addResource');

const confirmError = () => {
  inputIsInvalid.value = false;
};

const resetForm = () => {
  titleRef.value.value = '';
  descriptionRef.value.value = '';
  urlRef.value.value = '';
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
