<template>
  <header>
    <img src="../assets/img/logo-small.svg" alt="">
  </header>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style lang="scss">
@import "../assets/style/vars.scss";

header{
  background-color: $primary-color;
  height: 100px;
  display: flex;
  align-items: center;
  img{
    height: 70px;
    margin-left: 20px;
  }
}

</style>