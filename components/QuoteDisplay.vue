<template>
    <div v-if="quoteData">
      <p><strong>Quote:</strong> {{ quoteData.quote }}</p>
      <p><strong>Anime:</strong> {{ quoteData.anime }}</p>
      <p><strong>Character:</strong> {{ quoteData.character }}</p>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  const quoteData = defineProps(['quoteData']);
  </script>
  