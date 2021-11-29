<template>
  <div class="musical-genre">
    <select
      v-model="genre"
      @change="$emit('genre', select)"
      name="" id="">
      <option value="rock">Rock</option>
      <option value="pop">Pop</option>
      <option value="jazz">Jazz</option>
      <option value="metal">Metal</option>
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

  methods:{

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