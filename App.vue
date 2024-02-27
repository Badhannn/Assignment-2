<template>
  <div>
    <calculator @calculate="calculateResult"></calculator>
    <div v-if="result !== null" class="result">Result: {{ result }}</div>
    <div class="quote-container">
      <quote-display :quoteData="quoteData"></quote-display>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const result = ref(null);
const quoteData = ref(null);

const calculateResult = (data) => {
  const { num1, num2, operator } = data;
  switch (operator) {
    case '+':
      result.value = num1 + num2;
      break;
    case '-':
      result.value = num1 - num2;
      break;
    case '*':
      result.value = num1 * num2;
      break;
    case '/':
      result.value = num1 / num2;
      break;
    default:
      result.value = null;
  }
};

import { onMounted } from 'vue';
const fetchData = async () => {
  try {
    const response = await fetch('https://animechan.xyz/api/random');
    if (!response.ok) {
      throw new Error('Failed to fetch data');
    }
    const data = await response.json();
    quoteData.value = data;
  } catch (error) {
    console.error(error);
  }
};
onMounted(fetchData);
</script>

<style scoped>
.result {
  margin-top: 20px;
}
.quote-container {
  margin-top: 20px;
}
</style>
