<template>
  <div class="card">
    <img :src="card.poster" alt="">
    <h4>{{ card.title }}</h4>
    <h5>{{ card.author }}</h5>
  </div>
</template>

<script>
export default {
  name: 'Card',

  props: {

    card: Object,

  }

}
</script>

<style scoped lang="scss">
@import '../assets/styles/vars.scss';
  .card {
    height: 360px;
    width:200px;
    background-color: $color;
  }
  img {
    width: 100px;
  }
</style>
