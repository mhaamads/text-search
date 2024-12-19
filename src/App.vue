<template>
  <div class="min-h-screen text-white bg-stone-950 p-10">
    <h1 class=" text-5xl mb-5">Text Search</h1>
    <input v-model="search"
      class="h-10 text-sm w-full  focus:outline-none focus:border-none focus:ring-0 max-w-xs bg-stone-900 flex items-center px-5 rounded-md"
      placeholder="Search" />
    <div v-html="text" class="mt-10" />
   </div>
</template>
<script setup>
import { computed, ref } from 'vue';
const search = ref('')
const text = computed(() => {
  let value = `
  Your task is to create a search box where users can type in keywords or phrases, and your application returns results with the text being searched for highlighted. You can use any front-end framework you want (e.g. React, Angular, Vue.js, etc.).
No need for a backend to be integrated. Store an array of articles in a constant and make use of it.
It should look something like the image below.`
  if (!search.value) return value;
  const splitedText = value.split(new RegExp(`(${search.value})`, 'gi'));
  return splitedText.map(text => text.toLowerCase() === search.value.toLowerCase() ? `<mark>${text}</mark>` : text)
    .join('');
})
</script>

<style scoped></style>
