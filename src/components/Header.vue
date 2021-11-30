<template>
  <header>
    <img src="../assets/img/logo-small.svg" alt="">
    <Select 
      @genre="checkSearch"
      :genreToSelect="genreList"
    />
  </header>
</template>

<script>
import Select from "./Select.vue";

export default {
  name: "Header",

  data(){
    return{
      selectToGenre: "",
    }
  },

  props:{
    genreList: Array
  },

  components: {
    Select
  },

  methods: {
    checkSearch(genre){
      this.selectToGenre = genre;
      console.log(genre);
      return this.$emit("genreSel", this.selectToGenre);
    },

    genreToSelected(genre){
      this.genreList = genre;
      console.log("prova Header",this.genreList);
    }
  }
}
</script>

<style lang="scss">
@import "../assets/style/vars.scss";

header{
  background-color: $primary-color;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 20px;
  img{
    height: 70px;
    cursor: pointer;
  }
}
</style>