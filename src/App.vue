<template>

  <div>

    <HeaderComponent
    @startSearch="searchMovie"
    />
  
    <MainComponent
    :movie="filteredMovie"
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
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      apiParameters:{
        api_key: "4be099c980b79a719aecda19d1081396",
        language: "it-IT",
        query: ""
      },
      filteredMovie:[]
    }
  },

  methods:{
    apiRequest(){
      axios.get(this.apiUrl,{
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
      this.apiRequest()
    }

  },

  mounted(){
    this.apiRequest()
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
