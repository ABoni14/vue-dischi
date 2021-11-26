<template>
  <div class="loading container">
    <h2>{{LoadingTitle}}</h2>
    <div class="lds-ripple"><div></div><div></div></div>
  </div>
</template>

<script>
export default {
  name: "Loading",
  props:{
    LoadingTitle: String
  }
}
</script>

<style lang="scss">
.loading{
  height: 100%;
  display: flex;
  justify-content: center;
  flex-direction: column-reverse;
  align-items: center;
  color: white;
  h2{
    font-size: 30px;
  }
  .lds-ripple {
    display: inline-block;
    position: relative;
    width: 80px;
    height: 80px;
  }

  .lds-ripple div {
    position: absolute;
    border: 4px solid #fff;
    opacity: 1;
    border-radius: 50%;
    animation: lds-ripple 1s cubic-bezier(0, 0.2, 0.8, 1) infinite;
  }
  .lds-ripple div:nth-child(2) {
    animation-delay: -0.5s;
  }
  @keyframes lds-ripple {
    0% {
      top: 36px;
      left: 36px;
      width: 0;
      height: 0;
      opacity: 1;
    }
    100% {
      top: 0px;
      left: 0px;
      width: 72px;
      height: 72px;
      opacity: 0;
    }
  }
}
</style>