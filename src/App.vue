<template>

  <div>

    <HeaderComponent
    @startSearch="searchMovie"
    @filterItem="changeContentType"
    :research="filteredMovie"
    />
  
    <MainComponent
    :movie="filteredMovie"
    :series="filteredSeries"
    />

  </div>

</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from "./components/MainComponent.vue"
import axios from "axios"

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
},

  data(){
    return{
      apiUrlMovie: "https://api.themoviedb.org/3/search/movie",
      apiUrlTvSeries: "https://api.themoviedb.org/3/search/tv",
      apiUrlPopular: "https://api.themoviedb.org/3/movie/popular",
      apiParameters:{
        api_key: "4be099c980b79a719aecda19d1081396",
        language: "it-IT",
        query: ""
      },
      filteredMovie:[],
      filteredSeries: [],
      contentType: ""
    }
  },

  methods:{
    apiRequestMovie(){
      axios.get(this.apiUrlMovie,{
        params: this.apiParameters
      })
      .then(output => {
        console.log(output.data.results);
        this.filteredMovie = output.data.results
        console.log("ecco il log dei filtered movie:",this.filteredMovie);

      })
      .catch(error =>{
        console.log(error);
      })
    },

    searchMovie(searchInput){
      this.apiParameters.query = searchInput
      console.log("ecco cosa ha cercato l'utente:", this.apiParameters.query);
      this.apiRequestTvSeries()
      this.apiRequestMovie()
    },

    changeContentType(contentType){
      console.log(contentType);
      if (contentType === 'all') {
        this.apiRequestTvSeries()
        this.apiRequestMovie()
      } else if (contentType === 'tv'){
        this.apiRequestTvSeries()
        this.filteredMovie =[]
      } else{
        this.apiRequestMovie()
        this.filteredSeries =[]

      }
    },

    apiRequestTvSeries(){
      axios.get(this.apiUrlTvSeries,{
        params: this.apiParameters
      })
      .then(output => {
        console.log(output.data.results);
        this.filteredSeries = output.data.results
        console.log("ecco il log dei filtered tv series:",this.filteredSeries);

      })
      .catch(error =>{
        console.log(error);
      })
    },

  },

  mounted(){
  },

  computed:{
    SearchedMovie(){
      let movieSearched = this.output.data.results;
      console.log("ecco i film cercati:", movieSearched);

      return movieSearched
    }
  }
}
</script>

<style lang="scss">

@import "./assets/style/var";
@import "./assets/style/global";

</style>
