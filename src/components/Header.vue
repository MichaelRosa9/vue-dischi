<template>
  <header>
   <img src="../assets/img/spotify-logo.png" alt="">
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {

  }
}
</script>

<style scoped lang="scss">
@import '../assets/styles/vars.scss';

header {
  height: 70px;
  background-color: $color;
  display: flex;
  align-items: center;
}

img {
  height: 80%;
}
</style>