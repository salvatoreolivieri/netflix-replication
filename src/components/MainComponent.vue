<template>

<main>
  
  <div class="movie-container">

    <div
    v-for="(item,index) in movie" :key="index"
    class="movie-card">

      <h3>{{item.title}}</h3>
      <h4>{{item.original_title}}</h4>
      <p>{{item.original_language}}</p>
      <span>{{item.vote_count}}</span>

    </div>

  </div>

</main>
  
</template>

<script>
export default {
  name: "MainComponent.vue",
  props: {
    movie: Array
  }

}
</script>

<style lang="scss" scoped>

@import "../assets/style/var";

.movie-container{
  width: 80%;
  height: 300px;
  margin: 0 auto;
  border: 0.5px solid white;
  color: white;
  display: flex;
  flex-wrap: wrap;

  .movie-card{
    width: calc(100% / 4);
  border: 0.5px solid white;
  height: 100%;

  }
  
}


</style>