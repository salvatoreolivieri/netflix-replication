<template>

<main>

  <div v-if="series.length === 0" class="movie-container">
    <h1>I più popolari del momento</h1>
  </div>

  <div v-if="series.length === 0" class="movie-container">
    <CardComponent 
    v-for="(object,index) in this.popularMovie" :key="`popular${index}`"
    :item="object"
    />
  </div>

 

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
import axios from "axios"


export default {
    name: "MainComponent.vue",
    components: { CardComponent },
    props: {
        movie: Array,
        series: Array,
    },
    data() {
        return {
            urlImage: "https://image.tmdb.org/t/p/original/",
            apiUrlPopular: "https://api.themoviedb.org/3/movie/popular",
            apiParameters:{
              api_key: "4be099c980b79a719aecda19d1081396",
              language: "it-IT",
              query: ""
            },
            popularMovie:[]
        };
    },

    methods:{
      apiRequestPopular(){
      axios.get(this.apiUrlPopular,{
        params: this.apiParameters
      })
      .then(output => {
        console.log(output.data.results);
        this.popularMovie = output.data.results
        console.log("ecco il log dei popular movie:",this.popularMovie);

      })
      .catch(error =>{
        console.log(error);
      })
    },
    },

    mounted(){
      this.apiRequestPopular()
    }
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