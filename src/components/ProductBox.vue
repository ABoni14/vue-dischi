<template>
  <div class="box">
    <img :src="albums.poster" :alt="albums.title">
    <h3>{{albums.title}}</h3>
    <h5>{{albums.author}}</h5>
    <h5>{{albums.year}}</h5>
  </div>
</template>

<script>
export default {
  name: "ProductBox",
  props:{
    albums: Object
  }
}
</script>

<style lang="scss">
@import "../assets/style/vars.scss";

.box{
  width: calc(100% / 5 - 30px);
  margin: 15px;
  background-color: $primary-color;
  text-align: center;
  padding-bottom: 50px;
  padding: 15px;
  img{
    width: 100%;
    margin-bottom: 15px;
  }
  h3{
    font-size: 20px;
    color: white;
    margin-bottom: 10px;
    text-transform: uppercase;
  }
  h5{
    font-size: 15px;
    color: grey;
    font-weight: 400;
  }
}
</style>