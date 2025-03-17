<script setup>
import { ref } from 'vue'

const message = ref('Selamat pada belajar-!!')

const showAlert = () => {
  alert('Tombol ini diklik')
}

const isDisabled = ref (true)

const count = ref (8)
const isVisible = ref(false)
</script>

<template>
  <h1>{{ message }}</h1>

  <input v-model="message" placeholder="Ketikkan sesuatu..."/><br>
<br>
  <button @click="showAlert">Klik Aja</button>
  
  <button v-bind:disabled="isDisabled">Klik Aja</button>

  <p v-if="count > 10">Nilai terlalu besar</p>
  <p v-else-if="count > 5">Nilai berada di tengah</p>
  <p v-else>Nilai Kecil</p>

  <p v-show="isVisible">Teks ini dapat disembunyikan menggunakan v-Show</p>
  <button @click="isVisible = !isVisible">Tampilkan/Sembunyikan</button>
</template>

<style scoped>

</style>
