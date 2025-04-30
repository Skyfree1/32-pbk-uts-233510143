<template>
  <div class="container">
    <h1>Daftar Kegiatan</h1>

    <form @submit.prevent="tambahKegiatan">
      <input v-model="kegiatanBaru" placeholder="Tambahkan kegiatan baru" />
    </form>

    <ul>
      <li v-for="(kegiatan, index) in daftarKegiatan" :key="index">
        {{ kegiatan }}
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
    daftarKegiatan.value.push(kegiatanBaru.value)
    kegiatanBaru.value = ''
  }
}
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
}
input {
  padding: 8px;
  width: 70%;
}
button {
  padding: 8px 12px;
  margin-left: 8px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 8px 0;
  background: #f0f0f0;
  padding: 10px;
  border-radius: 4px;
}
</style>
