<template>
  <div class="container">
    <div>
      <FormSiswa @siswa-added="addSiswa" />
      <DaftarSiswa :daftar-siswa="daftarSiswa" :rata-rata="rataRata" />
    </div>
  </div>
</template>

<script>
import FormSiswa from '~/components/FormSiswa.vue'
import DaftarSiswa from '~/components/DaftarSiswa.vue'

export default {
  name: 'IndexPage',
  components: {
    FormSiswa,
    DaftarSiswa
  },
  data () {
    return {
      daftarSiswa: [],
      rataRata: null
    }
  },
  methods: {
    addSiswa (siswa) {
      this.daftarSiswa.push(siswa)
      this.calculateRataRata()
    },
    calculateRataRata () {
      const totalNilai = this.daftarSiswa.reduce((sum, siswa) => sum + siswa.nilai, 0)
      this.rataRata = totalNilai / this.daftarSiswa.length
    }
  }
}
</script>
