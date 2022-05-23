<template>

<main>
  
  <div class="movie-container">

    <div
    v-for="(item,index) in movie" :key="index"
    class="movie-card">

      <img :src= "`https://image.tmdb.org/t/p/original/${item.backdrop_path}`" alt="">

      <div class="info-container">
        <h4 style="margin-bottom: 10px">Titolo: "{{item.title}}"</h4>
        <h5 style="margin-bottom: 10px">Titolo Originale: "{{item.original_title}}"</h5>

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

        <span>Voto: {{item.vote_average}} / 10</span>
      </div>


    </div>

  </div>

</main>
  
</template>

<script>
export default {
  name: "MainComponent.vue",
  props: {
    movie: Array
  },
  data(){
    return{
      urlImage: "https://image.tmdb.org/t/p/original/"
    }
  },

  methods:{
    imgPreUrl(){

    }
  }



}
</script>

<style lang="scss" scoped>

@import "../assets/style/var";

.movie-container{
  width: 80%;
  height: 300px;
  margin: 0 auto;
  margin-top: 30px;
  color: white;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;

  .movie-card{
    width: calc((100% / 4) - 40px);
    height: 100%;
    margin-right: 10px;
    border: 1px solid white;
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
    height: 100%;
    padding: 20px;
    display: none;
  }


}


</style>