<template>
  <div class="musical-genre">
    <select
      v-model="genre"
      @change="$emit('genre', select)"
      name="" id="">
      <option value="" selected>Tutti</option>
      <option
        v-for="(genre, index) in genreToSelect"
        :key="index"
        :value="genre"
      >
        {{genre}}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "Select",

  data(){
    return{
      genre: ""
    }
  },

  props:{
    genreToSelect: Array
  },

  computed:{
    select(){
      return this.genre
    }
  }
}
</script>

<style lang="scss">
.musical-genre{
  select{
    font-size: 20px;
    padding: 10px 20px;
    font-weight: 700;
  }
}
</style>