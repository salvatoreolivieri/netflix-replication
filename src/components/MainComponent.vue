<template>

<main>

  <!-- films -->

  <div v-if="movie.length > 0" class="movie-container">
    <h1>Film</h1>
  </div>

  <div class="movie-container">

    <MovieCardComponent 
    v-for="(object) in movie" :key="object.id"
    :item="object"
    />

  </div>


  <!-- serie tv -->

  <div  v-if="series.length > 0" class="movie-container">
    <h1>Serie tv</h1>
  </div>

  <div class="movie-container">

    <SerieTvCardComponent
    v-for="(object) in series" :key="object.id"
    :item="object"
    />
    
  </div>

</main>
  
</template>

<script>
import MovieCardComponent from './MovieCardComponent.vue'
import SerieTvCardComponent from './SerieTvCardComponent.vue';

export default {
    name: "MainComponent.vue",
    props: {
        movie: Array,
        series: Array
    },
    data() {
        return {
            urlImage: "https://image.tmdb.org/t/p/original/",
        };
    },
    methods: {
        numberoStellePiene(average) {
            return Math.round(average / 2);
        },

        numeroStelleVuote(){
          return 5 - this.numberoStellePiene
        }
    },
    components: { MovieCardComponent, SerieTvCardComponent }
}
</script>

<style lang="scss">

@import "../assets/style/var";

svg{
  width: 20px;
}

.movie-container{
  width: 80%;
  margin: 0 auto;
  margin-top: 30px;
  color: white;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;

  .movie-card{
    width: calc((100% / 4) - 40px);
    height: 300px;
    margin-right: 10px;
    margin-bottom: 10px;
    position: relative;
    text-align: center;

    &:hover .info-container{
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    &:hover img{
      opacity: 0.5;
    } 


  }

  img{
    width: 100%;
    height: 100%;
    object-fit: cover;

  }

  .info-container{
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    padding: 20px;
    display: none;
  }


}


</style>