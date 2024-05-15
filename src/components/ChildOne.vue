<template>
  <div>
    <button @click="triggerEvent">Pancarkan Event</button>
  </div>
</template>

<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['response']);

const triggerEvent = () => {
  const message = 'Pesan dari Child One';
  emit('response', message);
};
</script>

<style scoped>
button {
  margin: 10px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  background-color: #4CAF50; /* Green */
  color: white;
  border: none;
  border-radius: 4px;
}
</style>
