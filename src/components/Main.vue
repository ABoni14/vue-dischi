<template>
  <main>
    <div 
      v-if="loading"
      class="container main-container">
      <ProductBox 
        v-for="(album, index) in albums"
        :key="index"
        :albums="album"/>
    </div>

    <Loading 
      v-else LoadingTitle="Albums Spotify loading..." />
  </main>
</template>

<script>
import axios from "axios";
import ProductBox from "./ProductBox.vue";
import Loading from "./Loading.vue";

export default {
  name: "Main",
  components: {
    ProductBox,
    Loading
  },
  data(){
    return{
      albums: [],
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      loading: true
    }
  },
  methods:{
    getApi(){
      axios.get(this.apiUrl)
        .then( r => {
          this.albums = r.data.response;
          this.loading = false
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
  min-height: calc(100vh - 100px);
  background-color: $secondary-color;
  .main-container{
    display: flex;
    flex-wrap: wrap;
    padding-top: 40px;
  }
}
</style>