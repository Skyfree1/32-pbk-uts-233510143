<template>
  <div class="container">
    <h1>Daftar Kegiatan</h1>
    <form @submit.prevent="tambahKegiatan" class="form-input">
      <input v-model="kegiatanBaru" placeholder="Masukkan kegiatan baru" class="input-besar" />
      <button type="submit" class="btn-tambah">Tambah</button>
    </form>

    <ul>
      <li v-for="(item, index) in daftarKegiatan" :key="index">
        <label class="kegiatan-label">
          <input type="checkbox" v-model="item.selesai" />
          <span :class="{ selesai: item.selesai }">{{ item.nama }}</span>
        </label>
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
  const nama = kegiatanBaru.value.trim()
  if (nama !== '') {
    daftarKegiatan.value.push({ nama, selesai: false })
    kegiatanBaru.value = ''
  }
}

function hapusKegiatan(index) {
  daftarKegiatan.value.splice(index, 1)
}
</script>

<style>

html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  font-family: sans-serif;
  color: white;
}

body {
  background-image: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1740&q=80');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
}

body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: -1;
}

.container {
  max-width: 600px;
  min-height: 100vh;
  margin: 0 auto;
  background-color: rgba(255, 255, 255, 0.1);
  padding: 2rem;
  border-radius: 10px;
  backdrop-filter: blur(5px);
}

.form-input {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
}

.input-besar {
  flex: 1;
  padding: 14px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 6px;
}

.btn-tambah {
  padding: 14px 24px;
  font-size: 16px;
  background-color: #2d8cf0;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 1rem;
}

li {
  background-color: rgba(255, 255, 255, 0.2);
  padding: 12px;
  margin-bottom: 6px;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
}

.kegiatan-label {
  display: flex;
  align-items: center;
  gap: 10px;
}

.selesai {
  text-decoration: line-through;
  color: #ddd;
}
</style>
