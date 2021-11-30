<template>
  <div>
    <Header
      @genreSel="getGenre"
      :genreList="genre"
    />
    <Main 
      :genreSelectet="genreSelected"
      @genreToPush="genreForHeader"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: 'App',
  components: {
    Header,
    Main
  },

  data(){
    return{
      genreSelected: "",
      genre: []
    }
  },

  methods:{
    getGenre(genre){
      this.genreSelected = genre;
      console.log("Sono in VUE APP", this.genreSelected);
    },

    genreForHeader(genre){
      this.genre = genre;
      console.log("provaApp", this.genre);
    }
  },

  
}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/utilities.scss";
@import "./assets/style/generals.scss";


</style>
