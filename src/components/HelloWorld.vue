<script setup>
import { ref, computed, watch, onMounted } from 'vue'

const message = ref('Selamat pada belajar-!!')

const showAlert = () => {
  alert('Tombol ini diklik')
}

const isDisabled = ref (true)

const count = ref (8)
const isVisible = ref(false)

//pertemuan5
const daftarBuah = ref(['Apel', 'Jeruk', 'Mangga']);

const harga = ref(100);
const diskon = ref(50);

const hargaSetelahDiskon = computed(() => {
  return harga.value - (harga.value * diskon.value / 100);
});

const email = ref('');
watch(email, (newValue) => {
  if(!newValue.includes('@')) {
    console.log('Alamat email tidak valid-!!');
  }
});

const myInput = ref(null);
const fokusInput = () => {
  if (myInput.value) {
    myInput.value.focus();
  }
};

onMounted(() => {
  console.log('Komponen telah dimuat!');
});

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

  <hr>
  <h1>Pertemuan5</h1>

  <ul>
    <li v-for="item in daftarBuah" :key="item">{{ item }}</li>
  </ul>

  <div>
    <p>Harga awal : {{ harga }}</p>
    <p>Diskon : {{ diskon }} %</p>
    <p>Harga setelah diskon : {{ hargaSetelahDiskon }}</p>
  </div>

  <div>
    <label for="email">Email : </label>
    <input type="email" id="email" v-model="email"/>
  </div>
<br>
  <div>
    <input ref="myInput" />
    <button @click="fokusInput">Fokus</button>
  </div>
</template>

<style scoped>

</style>
