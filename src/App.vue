<template>
  <div class="container">
    <h1>Daftar Kegiatan</h1>

    <!-- Input Tambah Kegiatan -->
    <form @submit.prevent="tambahKegiatan">
      <input v-model="kegiatanBaru" placeholder="Masukkan kegiatan baru" />
      <button type="submit">Tambah</button>
    </form>

    <!-- Daftar Kegiatan -->
    <ul>
      <li v-for="(item, index) in daftarKegiatan" :key="index">
        {{ item }}
        <button @click="hapusKegiatan(index)">Batal</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const kegiatanBaru = ref('')
const daftarKegiatan = ref([])

function tambahKegiatan() {
  if (kegiatanBaru.value.trim() !== '') {
    daftarKegiatan.value.push(kegiatanBaru.value.trim())
    kegiatanBaru.value = ''
  }
}

function hapusKegiatan(index) {
  daftarKegiatan.value.splice(index, 1)
}
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 2rem auto;
  font-family: sans-serif;
}

input {
  padding: 8px;
  width: 60%;
}

button {
  padding: 8px 12px;
  margin-left: 10px;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 1rem;
}

li {
  background-color: #f5f5f5;
  padding: 10px;
  margin-bottom: 5px;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li button {
  background-color: red;
  color: white;
  border: none;
  cursor: pointer;
  padding: 5px 10px;
  border-radius: 4px;
}
</style>
