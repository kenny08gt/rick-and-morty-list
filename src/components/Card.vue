<template>
  <div class="card shadow rounded-sm m-4">
    <div class="background"></div>
    <div class="content">
      <img :src="character.image" >
      <div class="w-full">
        <div class="text-left pt-2 w-32 text-white">
          <span class="text-sm text-white">
            <strong>{{ character.name}}</strong> <br>
            {{ character.species }} <br>
            <small> {{ character.origin ? character.origin.name : '' }}</small>
            </span>
        </div>
      </div>  
    </div>
    
  </div>
</template>
<style scoped>
  .card {
    padding: 20px;
    position: relative;
   cursor: pointer;
  }

  .card:hover .background {
    background-color: rgba(255, 255, 255, .35);  
  }

  .background {
   background-color: rgba(255, 255, 255, .15);  
    backdrop-filter: blur(5px);
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
     transition: background-color 0.3s;
  }

  .content {
    position: relative;
  }

  img {
    width: 150px;
    border-radius: 8px;
  }
</style>
<script>
  export default {
    name: 'card',
    props: {
      character: Object
    },
    data() {
      return {
        image: "./assets/placeholder.jpeg",
        loaded: false,
      }
    },
    mounted () {
    
    }
  }
</script>
