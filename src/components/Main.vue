<template>
  <main>
    <div class="container flex-center-between wrap">
      <Card 
        v-for="(card, index) in cards" :key="index" 
        :card="card"
      />
      <div  v-for="(card, index) in cards" :key="index">
      </div>
    </div>
  </main>
</template>

<script>

import Card from '@/components/Card.vue';
import axios from 'axios';

export default {
  name: 'Main',
  data(){
    return {
      axios,
      cards: []
    }
  },
  created() {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music")
    .then(result => {      
      this.cards = result.data.response;
      console.log(this.cards);
    })
    .catch(err => {
      console.log(err);
    });
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
  height: calc(100vh - #{$header-height});
}


</style>
