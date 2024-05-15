<template>
  <div>
    <!-- Bagian pertama -->
    <div class="container">
      <h1>{{ parentComponentTitle }}</h1> <!-- Memperbarui judul -->
      <div class="child-container">
        <!-- Memasukkan ChildOne -->
        <ChildOne @response="handleChildOneResponse" />
        <!-- Memasukkan ChildTwo -->
        <ChildTwo @response="handleChildTwoResponse" />
      </div>
      <div class="response-container">
        <!-- Menampilkan pesan dari ChildOne -->
        <p>{{ childOneResponse }}</p>
        <!-- Menampilkan peringatan dari ChildTwo -->
        <p>{{ childTwoResponse }}</p>
      </div>
    </div>
    <!-- Bagian kedua -->
    <div class="container">
      <h1>Parent Component</h1>
      <SlotComponent>
        <!-- Isi slot dengan konten khusus untuk ditampilkan -->
        <div>
          <p>Konten khusus untuk slot:</p>
          <!-- Ganti tombol dengan input teks -->
          <input type="text" v-model="slotContent" @keydown.enter="handleEnter" placeholder="Masukkan konten" />
          <button @click="changeSlotContent">Ubah Konten Slot</button>
          <button @click="resetTitle">Reset Judul</button> <!-- Tombol untuk mengembalikan judul ke nilai semula -->
          <button @click="clearInput">Hapus</button>
        </div>
      </SlotComponent>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ChildOne from './components/ChildOne.vue';
import ChildTwo from './components/ChildTwo.vue';
import SlotComponent from './components/SlotComponent.vue';

const parentComponentTitle = ref('Parent Component'); // Variabel untuk menyimpan judul parent component
const childOneResponse = ref(''); // Variabel untuk menyimpan pesan dari ChildOne
const childTwoResponse = ref(''); // Variabel untuk menyimpan peringatan dari ChildTwo
const slotContent = ref(''); // Variabel untuk menyimpan konten slot
const originalTitle = 'Parent Component'; // Nilai asli dari judul parent component

const handleChildOneResponse = (message) => {
  childOneResponse.value = message; // Menetapkan pesan dari ChildOne
};

const handleChildTwoResponse = (warningText) => {
  childTwoResponse.value = warningText; // Menetapkan peringatan dari ChildTwo
};

const changeSlotContent = () => {
  // Mengubah konten slot sesuai dengan nilai dari input teks
  console.log('Konten slot diubah menjadi:', slotContent.value);
  // Mengubah judul parent component
  parentComponentTitle.value = slotContent.value;
};

const resetTitle = () => {
  // Mengembalikan judul parent component ke nilai semula
  parentComponentTitle.value = originalTitle;
};

const handleEnter = () => {
  // Logika untuk menanggapi saat tombol "Enter" ditekan
  console.log('Tombol "Enter" ditekan');
};

const clearInput = () => {
  // Mengosongkan nilai input
  slotContent.value = '';
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  border: 2px solid #ccc;
  border-radius: 8px;
  text-align: center;
}

.child-container {
  display: flex;
  justify-content: center;
}

.response-container {
  margin-top: 20px;
}

.response-container p {
  margin-top: 10px;
}
</style>
