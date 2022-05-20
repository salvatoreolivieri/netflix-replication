<template>

  <HeaderComponent
  @startSearch="cercaFilm"
  />

</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import axios from "axios"

export default {
  name: 'App',
  components: {
    HeaderComponent,
  },

  data(){
    return{
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      apiParameters:{
        api_key: "4be099c980b79a719aecda19d1081396",
        language: "it-IT",
        query: "ritorno al futuro"
      },
    }
  },

  methods:{
    apiRequest(){
      axios.get(this.apiUrl,{
        params: this.apiParameters
      })
      .then(output => {
        console.log(output.data);
      })
      .catch(error =>{
        console.log(error);
      })
    },

    cercaFilm(searchInput){
      this.apiParameters.query = searchInput
      console.log("ecco cosa ha cercato l'utente:", this.apiParameters.query);
      this.apiRequest()
    }

  },

  mounted(){
    this.apiRequest()
  },

  computed:{

  }
}
</script>

<style lang="scss">

@import "./assets/style/var";
@import "./assets/style/global";

</style>
