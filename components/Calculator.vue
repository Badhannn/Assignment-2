<template>
  <div>
    <input type="number" v-model="num1" placeholder="Enter first number" />
    <input type="number" v-model="num2" placeholder="Enter second number" />
    <select v-model="operator">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    <button @click="calculate">Calculate</button>
  </div>
</template>

<script setup>
import { ref, defineProps, defineEmits } from 'vue';

const { emit } = defineEmits(['calculate']);
const { num1, num2, operator } = defineProps(['num1', 'num2', 'operator']);
const calculate = () => {
  if (!num1.value || !num2.value || !operator.value) return;
  emit('calculate', { num1: Number(num1.value), num2: Number(num2.value), operator: operator.value });
};
</script>
