<template>

<main>

  <!-- films -->

  <div v-if="movie.length > 0" class="movie-container">
    <h1>Film</h1>
  </div>

  <div class="movie-container">

    <CardComponent 
    v-for="(object) in movie" :key="object.id"
    :item="object"
    />

  </div>


  <!-- serie tv -->

  <div  v-if="series.length > 0" class="movie-container">
    <h1>Serie TV</h1>
  </div>

  <div class="movie-container">

    <CardComponent
    v-for="(object) in series" :key="object.id"
    :item="object"
    />
    
  </div>

</main>
  
</template>

<script>
import CardComponent from './CardComponent.vue';

export default {
    name: "MainComponent.vue",
    components: { CardComponent },
    props: {
        movie: Array,
        series: Array
    },
    data() {
        return {
            urlImage: "https://image.tmdb.org/t/p/original/",
        };
    },
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
      opacity: 0.3;
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