<script setup lang="ts">
import { ref, onMounted } from 'vue'
import axios from 'axios'

const message = ref("Loading...")

onMounted(async () => {
  try {
    const response = await axios.get("https://localhost:7265/api/hello")
    message.value = response.data.message
  } catch (err) {
    message.value = "Error fetching message"
    console.error(err)
  }
})
</script>

<template>
  <div>
    <h1>{{ message }}</h1>
  </div>
</template>