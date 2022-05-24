<template>

    <div
    class="movie-card">

      <img
      v-if="item.backdrop_path === null"
      src="../assets/img/not-found.png" alt="">

      <img
      v-else
      :src= "`https://image.tmdb.org/t/p/original/${item.backdrop_path}`" alt="">

      <div class="info-container">
        <h4 style="margin-bottom: 10px">Titolo: "{{item.name}}"</h4>
        <h5 style="margin-bottom: 10px">Titolo Originale: "{{item.original_name}}"</h5>

        <div style="margin-bottom: 10px"
        v-if="item.original_language === 'it'" >
        <img style="width: 50px" src="../assets/img/italy.png" alt="">
        </div>

        <div style="margin-bottom: 10px"
        v-else-if="item.original_language === 'en'" >
        <img style="width: 50px" src="../assets/img/english.png" alt="">
        </div>

        <p style="margin-bottom: 10px"
        v-else>Lingua: {{item.original_language}}
        </p>

        <StellaPienaComponent
        />

        <StellaVuotaComponent
        />

      </div>


  </div>
</template>

<script>

import StellaPienaComponent from './StellaPienaComponent.vue';
import StellaVuotaComponent from './StellaVuotaComponent.vue';

export default {
    name: "SerieTvCardComponent",
    components: { StellaPienaComponent, StellaVuotaComponent },
    props:{
      item: Object
    }
}

</script>

<style lang="scss">

</style>