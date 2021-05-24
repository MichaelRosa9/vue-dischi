<template>
  <main>
    <div v-if="!loading" class="container flex-center-between wrap gap-40">
      <Card class="basis-20-perc"
        v-for="(card, index) in cards" :key="index" 
        :card="card"
      />      
    </div>

    <Loader />
  </main>
</template>

<script>

import axios from 'axios';
import Card from '@/components/Card.vue';
import Loader from '@/components/Loader.vue';
export default {
  name: 'Main',
  data(){
    return {
      axios,
      cards: [],
      loading: true
    }
  },
  created() {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music")
    .then(result => {      
      this.cards = result.data.response;
      this.loading = false;
      console.log(this.cards);
    })
    .catch(err => {
      console.log(err);
    });
  },
  components: {
    Card,
    Loader
  }
}
</script>

<style scoped lang="scss">
@import '../assets/styles/vars.scss';

main {
  background-color: #1A2833;
  height: calc(100vh - #{$header-height});
  overflow: auto;
}




</style>
