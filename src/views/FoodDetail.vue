<template>
    <div class="food-detail">
        <Navbar />
        <div class="container">

            <!-- Breadcrumb -->
            <div class="row mt-5">
                <div class="col">
                    <nav aria-label="breadcrumb">
                    <ol class="breadcrumb mt-5">
                        <li class="breadcrumb-item"><router-link to="/" class="text-dark">Home</router-link></li>
                        <li class="breadcrumb-item"><router-link to="/Foods" class="text-dark">Foods</router-link></li>
                        <li class="breadcrumb-item active" aria-current="page">Food Order</li>
                    </ol>
                    </nav>
                </div>
            </div>

            <div class="row mt-4">
                <div class="col-md-6">
                    <img :src="'../assets/img/' + products.gambar" alt="" class="img-fluid shadow">
                </div>
                <div class="col-md-6">
                    <h2><strong>{{ products.nama }}</strong></h2>
                    <hr>
                    <h4>Harga : <strong>Rp. {{ products.harga }}</strong></h4>
                    <form action="" class="mt-4" v-on:submit.prevent>
                        <div class="form-group">
                            <label for="jumlah_pemesanan">Jumlah Pesan</label>
                            <input type="number" class="form-control" v-model="pesan.jumlah_pemesanan">
                        </div>
                        <div class="form-group">
                            <label for="keterangan">Keterangan</label>
                            <textarea class="form-control" placeholder="Keterangan spt: Pedes, Nasi Setengah" v-model="pesan.keterangan"></textarea>
                        </div>
                        <button type="submit" class="btn btn-success" @click="pemesanan"><b-icon-cart></b-icon-cart>Pesan</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
import axios from 'axios'

export default {
  name: 'FoodDetail',
  components: {
    Navbar
  },
  data () {
    return {
      products: {},
      pesan: {}
    }
  },
  methods: {
    setProduct (data) {
      this.products = data
    },
    pemesanan () {
      if (this.pesan.jumlah_pemesanan) {
        this.pesan.products = this.products
        axios
          .post('http://localhost:3000/keranjangs', this.pesan)
          .then(() => {
            this.$router.push({ path: '/keranjang' })
            this.$toast.success('Sukses Masuk Keranjang.', {
              type: 'success',
              position: 'top-right',
              duration: 3000,
              dismissible: true
            })
          })
          .catch((err) => console.log(err))
      } else {
        this.$toast.error('Jumlah Pesanan Harus di-Isi ', {
          type: 'error',
          position: 'top-right',
          duration: 3000,
          dismissible: true
        })
      }
    }
  },
  mounted () {
    axios
      .get('http://localhost:3000/products/' + this.$route.params.id)
      .then((response) =>
        // handle success
        this.setProduct(response.data)
      )
      .catch((error) =>
        // handle Error
        console.log(error)
      )
  }
}
</script>

<style>

</style>
