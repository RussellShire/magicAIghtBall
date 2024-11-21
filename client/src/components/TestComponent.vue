<script setup>
import { ref, onMounted } from 'vue';

const message = ref('');

const fetchData = async () => {
  try {
    const response = await fetch('/api/test');
    const data = await response.json();
    message.value = data.message;
  } catch (error) {
    console.error('Error:', error);
  }
};

onMounted(() => {
  fetchData();
});
</script>

<template>
  <div>
    <h2>Message from API: {{ message }}</h2>
  </div>
</template>
