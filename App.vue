<template>
   <div>
      <h1>Characters</h1>
      <div class="content">
        <div class="content-characters" 
        v-for="character in characters" 
        :key="character.id">
        <div class="character">
          <img :src="character.image" alt="">
        <div class="info-character">
          <h2> {{ character.name}}</h2>
          <h4> {{ character.species}}</h4>
          <h4> {{ character.status}}</h4>
        </div>
        </div>
    </div>
   </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data(){
    return {
      characters: []
    }
  },
  mounted(){
    this.getTodos();
  },
  methods: {
    getTodos(){
      axios
      .get('https://rickandmortyapi.com/api/character/')
      .then(res => {
        (this.characters = res.data.results)
      })
      .catch(e => {
        console.log(e)
      })
    }
  },
}
</script>

<style>

</style>
