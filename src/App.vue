<template>
  <character-list />
</template>

<script>
import CharacterList from './components/CharacterList.vue'
export default {
  name: 'App',
  components: {
    CharacterList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
      background-attachment: fixed;
    background-image: url(./assets/rick-and-morty-breaking-bad-wallpaper-1152x768_36.png);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
}
</style>
