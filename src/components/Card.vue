<template>
  <div class="card">
    <img :src="card.poster" alt="">
    <h4>{{ card.title }}</h4>
    <h5>{{ card.author }}</h5>
    <h6>{{ card.year }}</h6>
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
    height: 400px;
    background-color: $color;
    padding: 25px;
    text-transform: uppercase;
    text-align: center;
  }

  h4 {
    margin-top: 10px;
    margin-bottom: 20px;
    font-size: 20px;
    color: white
  }

  h5,
  h6 {
    color: grey
  }
  img {
    width: 100%;
  }
</style>
