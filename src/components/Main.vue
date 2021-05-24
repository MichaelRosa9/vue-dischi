<template>
  <main>
    <div class="container">
      <Card />

    </div>
  </main>
</template>

<script>
import Card from '@/components/Card.vue'
export default {
  name: 'Main',
  props: {

  },
  components: {
    Card
  }
}
</script>

<style scoped lang="scss">
@import '../assets/styles/vars.scss';

main {
  background-color: #1A2833;
  height: calc(100vh - #{$header-heigth});

}
</style>
