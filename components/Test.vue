<template>
  <div class="container">
    <pre>{{ products }}</pre>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const products = ref([]);

onMounted(async () => {
  try {
    const response = await axios.get(
      `https://66856627b3f57b06dd4c9bbf.mockapi.io/products/:endpoint`
    );
    // Assuming the API returns an array directly (response.data should be an array)
    products.value = response.data.map((product) => ({
      ...product,
      liked: false,
      shopped: false,
    }));
  } catch (error) {
    console.error("Error fetching products:", error);
  }
});
</script>
