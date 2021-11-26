<template>
  <main>
    <div class="container main-container">
      <ProductBox 
        v-for="(album, index) in albums"
        :key="index"
        :albums="album"/>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import ProductBox from "./ProductBox.vue";

export default {
  name: "Main",
  components: {
    ProductBox
  },
  data(){
    return{
      albums: [],
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music"
    }
  },
  methods:{
    getApi(){
      axios.get(this.apiUrl)
        .then( r => {
          this.albums = r.data.response;
        })
        .catch( e => {
          console.log(e);
        })
    }
  },
  mounted(){
    this.getApi();
  }
}
</script>

<style lang="scss">
@import "../assets/style/vars.scss";

main{
  height: calc(100vh - 100px);
  background-color: $secondary-color;
  .main-container{
    display: flex;
    flex-wrap: wrap;
    padding-top: 40px;
  }
}
</style>