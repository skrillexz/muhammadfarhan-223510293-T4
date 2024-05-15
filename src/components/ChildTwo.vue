<template>
  <div>
    <!-- Element yang memicu event -->
    <button @click="triggerEvent">Pancarkan Event</button>
  </div>
</template>

<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['response']);

// Fungsi untuk memicu event dan menampilkan peringatan
const triggerEvent = () => {
  const warningText = 'Peringatan dari Child Two!';
  alert(warningText); // Menampilkan peringatan menggunakan alert
  emit('response', warningText); // Memancarkan event ke parent dengan teks peringatan
};
</script>

<style scoped>
/* Gaya CSS sesuai kebutuhan */
button {
  margin: 10px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  background-color: #f44336; /* Red */
  color: white;
  border: none;
  border-radius: 4px;
}
</style>
