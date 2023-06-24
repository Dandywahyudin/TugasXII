<template>
  <div class="container">
    <h1 class="mt-5">
      Daftar Siswa
    </h1>
    <table class="table mt-3">
      <thead>
        <tr>
          <th>No Induk</th>
          <th>Nama Siswa</th>
          <th>Nilai Tugas</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(siswa, index) in daftarSiswa" :key="index">
          <td>{{ siswa.noInduk }}</td>
          <td>{{ siswa.namaSiswa }}</td>
          <td>{{ siswa.nilaiTugas }}</td>
        </tr>
      </tbody>
    </table>
    <p class="mt-10" />
    <h5>Rata-rata Nilai Tugas :  {{ rataRataNilai }} </h5>
  </div>
</template>

<script>
export default {
  props: {
    daftarSiswa: {
      type: Array,
      required: true
    }
  },
  computed: {
    rataRataNilai () {
      if (this.daftarSiswa.length === 0) {
        return 0
      }

      const totalNilai = this.daftarSiswa.reduce((sum, siswa) => {
        return sum + parseInt(siswa.nilaiTugas)
      }, 0)

      const rataRata = totalNilai / this.daftarSiswa.length

      return isNaN(rataRata) ? 0 : parseFloat(rataRata.toFixed(2))
    }
  }
}
</script>
