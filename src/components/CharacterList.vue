<template >
  <div class="relative">
    <h1 class="text-white text-xl pt-5">Rick and Morty API</h1>
    <div class="flex flex-wrap justify-center content-between">
        <card v-for="character in characters" :key="character.id" :character="character"/>
    </div>
  </div>
</template>
<style scoped>
  .loading {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: white;
  }
</style>
<script>
import Card from './Card.vue';
  const axios = require('axios');
  export default {
  components: { Card },
    name: 'characterList',
    data() {
      return {
        characters: [],
        next_page: null,
        loading: false,
      }
    },
    beforeMount(){
      this.loading = true;
      axios
      .get('https://rickandmortyapi.com/api/character/')
      .then(response => {
        this.characters = response.data.results; 
        this.next_page = response.data.info.next;
        this.loading = false;
      })
    },
    mounted () {
      this.getNextUser();
    },
    methods:{
        getNextUser() {
          window.onscroll = () => {
            let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight === document.documentElement.offsetHeight;
            if (bottomOfWindow && this.next_page) {
              this.loading = true;
              axios
              .get(this.next_page)
              .then(response => {
                this.characters.push(...response.data.results);
                this.next_page = response.data.info.next;
                this.loading = false;
              });
            }
          }
        }
    }
  }
</script>
