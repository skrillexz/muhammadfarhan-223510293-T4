<template>
  <div class="slot" :style="{ borderColor: borderColor }">
    <h3>Slot Component</h3>
    <div class="slot-content">
      <div class="slot-slot">
        <slot>
          <!-- Konten default untuk slot jika tidak ada yang disisipkan -->
          <p>Ini adalah konten slot default.</p>
        </slot>
      </div>
      <button @click="changeColor">Ubah Warna</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SlotComponent',
  data() {
    return {
      borderColor: '#999'
    };
  },
  methods: {
    changeColor() {
      // Mengubah warna bingkai secara acak
      this.borderColor = '#' + Math.floor(Math.random()*16777215).toString(16);
    }
  }
}
</script>

<style scoped>
.slot {
  border: 2px solid;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
}

.slot-content {
  margin-top: 10px;
}

.slot-slot {
  margin-bottom: 10px;
}

button {
  margin-top: 10px;
  padding: 8px 16px;
  font-size: 14px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>
