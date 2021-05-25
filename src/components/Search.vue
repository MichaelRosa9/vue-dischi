<template>
    
      <form action="">
        <input type="text" placeholder="Search..."
          v-model.trim="text"
          @keyup.enter="searchText()"
        >
        <button @click.prevent="searchText()">Search</button>
        <button @click.prevent="reset()">Reset</button>
      </form>

</template>

<script>



export default {
  name: 'Search',  
  components: {

  },
  data(){
    return{
      text: ''
    }
  },
  methods: {
    searchText(){
      this.$emit('searchText', this.text);
    },
    reset(){
      this.text='';
      this.$emit('resetText', this.text);
    }
  }
}
</script>

<style scoped lang="scss">
@import '../assets/styles/vars.scss';

form {
  input,
  button {
    height: 35px;
    margin-right: 17px;
    border: none;
    border-radius: 4px;
    padding: 5px 10px;
    box-shadow: 0 0 2px rgba( #000000, .1);
  }

  input {
    background-color: lightgrey;
    outline: none;
    width: 250px;
  }

  button {
    color: rgb(43, 41, 41);
    background-color: grey;
    &:hover {
      opacity: .9;
      color: lightgrey;
      cursor: pointer;
    }
  }

}

</style>