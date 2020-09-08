<template>
  <div class="hero">

    <!-- Desktop -->
      <div class="d-none d-md-block">
        <div class="row mt-4 ">
            <div class="col-md-6">
                <div class="d-flex h-100">
                  <div class="justify-content-center align-self-center">
                    <h2><strong>Delicious Food Menu</strong> <br> in Your Gadget</h2>
                    <p>Pilih dan Pesan Makanan Favorite Anda</p>
                    <router-link class="btn btn-lg btn-success" to="/Foods"><b-icon-arrow-bar-right></b-icon-arrow-bar-right>Pesan</router-link>
                  </div>
                </div>
            </div>
            <div class="col-md-6">
              <img src="../assets/img/Hero.png" width="100%" alt="Pict">
            </div>
        </div>
      </div>
    <!-- Mobile -->
      <div class="d-sm-block d-md-none">
        <div class="row mt-4 ">
            <div class="col-md-6">
              <img src="../assets/img/Hero.png" width="100%" alt="Pict">
            </div>
            <div class="col-md-6 mb-3">
                <div class="d-flex h-100">
                  <div class="justify-content-center align-self-center">
                    <h2><strong>Delicious Food Menu</strong> <br> in Your Gadget</h2>
                    <p>Pilih dan Pesan Makanan Favorite Anda</p>
                    <button class="btn btn-lg btn-success"><b-icon-arrow-bar-right></b-icon-arrow-bar-right>Pesan</button>
                  </div>
                </div>
            </div>
        </div>
      </div>
    </div>

</template>

<script>
export default {
  name: 'Hero'
}
</script>

<style>

</style>
