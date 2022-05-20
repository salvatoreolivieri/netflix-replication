<template>

<header>
  <div class="img-container">
    <img src="../assets/img/netflix-logo.png" alt="">
  </div>

  <div>
    <select>
      <option value="">Serie Tv</option>
      <option value="">Film</option>
    </select>
  </div>

  <div>
    <input type="text" placeholder="Search">
  </div>

</header>
  
</template>

<script>
export default {
  name: "HeaderComponent.vue"
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
    }
  }

  select{
    border: none;
    padding: 10px;
    border-radius: 5px;
    background-color: $secondary-color;
    color: white;
    font-size: 16px
  }

  input{
    border: none;
    padding: 5px;
    background-color: $secondary-color;
    color: white;
    border-bottom: 1px solid $primary-color;
    


    &:focus{
      outline: none;
    } 
  }
  
}

</style>