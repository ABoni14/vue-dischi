<template>
  <main>
    <div 
      v-if="loading"
      class="container main-container">
      <ProductBox 
        v-for="(album, index) in genreFilter"
        :key="index"
        :albums="album"
        />
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
      genre: "",
      genresToPush: [],
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      loading: false
    }
  },

  props:{
    genreSelectet: String
  },

  methods:{
    getApi(){
      axios.get(this.apiUrl)
        .then( r => {
          this.albums = r.data.response;
          this.loading = true;
          console.log("prova",this.genreSelectet);
          this.albums.forEach(album => {
            if(!this.genresToPush.includes(album.genre)){
              this.genresToPush.push(album.genre)
            }
          })
          this.$emit("genreToPush", this.genresToPush)
        })
        .catch( e => {
          console.log(e);
        })
    },
  },

  mounted(){
    this.getApi();
  },

  computed:{
    genreFilter(){
      if(this.genreSelectet === ""){
        return this.albums
      } else{
        let albumFilter = [];
        for(let i = 0; i < this.albums.length - 1; i++){
          if(this.albums[i].genre.toUpperCase().includes(this.genreSelectet.toUpperCase())){
            albumFilter.push(this.albums[i])
          }
        }
        return albumFilter
      }
    }
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