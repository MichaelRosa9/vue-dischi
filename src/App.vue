<template>
  <div id="app">
    <header>
      <img src="@/assets/img/spotify-logo.png" alt="">
      <div class="container flex-center-end">
        <Search @searchText="compareText" @resetText="resetCards"/>
      </div>
    </header>
    <main>
      <div v-if="!loading" class="container flex-center-evenly wrap gap-40">
        <Card class="basis-20-perc"
          v-for="(card, index) in filtedCards" :key="index" 
          :card="card"       
        />      
      </div>

      <Loader v-else />
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import Search from '@/components/Search.vue'
import Card from '@/components/Card.vue';
import Loader from '@/components/Loader.vue';

export default {
  name: 'App',  
  components: {
    Search,
    Card,
    Loader
  },
  data(){
    return {
      axios,
      cards: [],
      loading: true,
      text:'',
    }
  },
  created() {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music")
    .then(result => {      
      this.cards = result.data.response;
      this.loading = false;
    })
    .catch(err => {
      console.log(err);
    });
  },
  computed: {
    filtedCards(){
      return this.cards.filter(card => {
       if(card.title.toLowerCase().includes(this.text.toLowerCase())){
        return card.title.toLowerCase().includes(this.text.toLowerCase());
       }else if(card.author.toLowerCase().includes(this.text.toLowerCase())){
         return card.author.toLowerCase().includes(this.text.toLowerCase());
       }
      })
    }
  },
  methods: {
    compareText(event){
      
      this.text = event;
    },
    resetCards(event){
      this.text = event;
    }
  }
}
</script>

<style lang="scss">
@import "~@fontsource/montserrat/index.css";
@import './assets/styles/general.scss';
@import './assets/styles/utilities.scss';

@import './assets/styles/vars.scss';

header {
  position: relative;
  height: $header-height;
  background-color: $color;  
  
  img {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    height: 80%;
  }
}

main {
  background-color: #1A2833;
  height: calc(100vh - #{$header-height});
  overflow: auto;
}
</style>
