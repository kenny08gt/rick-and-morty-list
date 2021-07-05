<template >
  <div>
    <h1 class="text-white text-xl pt-5">Rick and Morty API</h1>
    <div class="flex flex-wrap justify-center content-between">
        <card v-for="character in characters" :key="character.id" :character="character"/>
    </div>
  </div>
</template>
<script>
import Card from './Card.vue';
  const axios = require('axios');
  export default {
  components: { Card },
    name: 'characterList',
    data() {
      return {
        characters: null,
      }
    },
    mounted () {
      axios
      .get('https://rickandmortyapi.com/api/character')
      .then(response => (this.characters = response.data.results))
    }
  }
</script>
