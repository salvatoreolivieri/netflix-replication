<template>

<header>
  <div class="img-container">
    <img @click="reloadPage" src="../assets/img/netflix-logo.png" alt="">
  </div>

  <div>
    <select
    @change="$emit('filterItem', contentType)"
    >
      <option value="">All</option>
      <option value="">Tv Series</option>
      <option value="">Movies</option>
    </select>
  </div>

  <div>
    <input
    @keyup.enter="startSearch"
    v-model="searchInput"
    type="text" placeholder="Search">
  </div>

</header>
  
</template>

<script>
export default {
  name: "HeaderComponent.vue",
  data(){
    return{
      searchInput: ""
    }
  },

  methods: {
    reloadPage() {
      window.location.reload();
    },
    startSearch(){
      this.$emit('startSearch', this.searchInput);
      this.searchInput = ""

    }
  }
}
</script>

<style lang="scss" scoped>

@import "../assets/style/var";

header{
  height: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0px 20px;
  background-color: $secondary-color;

  .img-container{
    width: 200px;

    img{
      width: 100%;
      cursor: pointer;
    }
  }

  select{
    border: none;
    padding: 10px;
    border-radius: 5px;
    background-color: $secondary-color;
    color: white;
    font-size: 18px
  }

  input{
    border: none;
    padding: 10px;
    background-color: $secondary-color;
    color: white;
    border-bottom: 0.5px solid $primary-color;
    font-size: 16px;

    &:focus{
      outline: none;
    } 
  }
  
}

</style>