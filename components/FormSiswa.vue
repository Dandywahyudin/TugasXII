<template>
  <div class="container">
    <h1>
      Form Nilai Tugas Siswa
    </h1>
    <form @submit.prevent="addSiswa">
      <div class="form-group">
        <label for="noInduk">No Induk Siswa :</label>
        <input id="noInduk" v-model="noInduk" type="text" required class="form-control col-sm-4">
      </div>
      <div class="form-group">
        <label for="namaSiswa">Nama Siswa :</label>
        <input id="namaSiswa" v-model="namaSiswa" type="text" required class="form-control col-sm-4">
      </div>
      <div class="form-group">
        <label for="nilaiTugas">Nilai Tugas :</label>
        <input id="nilaiTugas" v-model="nilaiTugas" type="number" required class="form-control col-sm-4">
      </div>
      <button type="submit" class="btn btn-primary">
        Tambah
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      noInduk: '',
      namaSiswa: '',
      nilaiTugas: null
    }
  },
  methods: {
    addSiswa () {
      const siswa = {
        noInduk: this.noInduk,
        namaSiswa: this.namaSiswa,
        nilaiTugas: this.nilaiTugas
      }
      this.$emit('siswa-added', siswa)
      this.noInduk = ''
      this.namaSiswa = ''
      this.nilaiTugas = null
    }
  }
}
</script>

<style>
.h1 {
  text-align: center;
}
</style>
