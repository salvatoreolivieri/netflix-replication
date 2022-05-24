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
        <h4 style="margin-bottom: 10px">Titolo: "{{item.title || item.name}}"</h4>
        <h5 style="margin-bottom: 10px">Titolo Originale: "{{item.original_title || item.original_name}}"</h5>

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

        <div>
          <StellaPienaComponent
          v-for="(number, index) in numberoStellePiene()" :key="`piena${index}`"
          />
          
          <StellaVuotaComponent
          v-for="(number, index) in 5 - numberoStellePiene()" :key='`vuota${index}`'
          />
        </div>

      </div>


  </div>
</template>

<script>

import StellaPienaComponent from './StellaPienaComponent.vue';
import StellaVuotaComponent from './StellaVuotaComponent.vue';

export default {
    name: "CardComponent",
    components: { StellaPienaComponent, StellaVuotaComponent },
    props:{
      item: Object
    },
      methods: {
        numberoStellePiene() {
            return Math.round(this.item.vote_average / 2);
        },

        numeroStelleVuote(){
          return 5 - this.numberoStellePiene
        }
    },
}

</script>

<style lang="scss">

</style>