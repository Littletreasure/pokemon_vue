<template>
  <div id="app">
    <header class="App-header">
          <h1>Pokemon</h1>
    </header>
    <search v-on:search="getPokemon($event)" />
    <contents v-if="content" v-bind:pokemon="pokemon" />
  </div>
</template>

<script>
import search from './components/search.vue';
import contents from './components/contents.vue';

export default {
  name: 'App',
  components: {
    'search': search,
    'contents': contents
  },
  data() {
    return {
     pokemon: {
      name: '',
      id: 0,
      abilities: [],
      picture: '',
      habitat: '',
      colour: ''
     },
     content: false
    }
    
  },
  methods: {
    getPokemon: function(input) {
      this.axios.get("https://pokeapi.co/api/v2/pokemon/" + input)
      .then(pokemon => {
        return Promise.all([
          pokemon,
          this.axios.get(
            "https://pokeapi.co/api/v2/pokemon-species/" + pokemon.data.id
          )
        ]);
      })
      .then(response => {
        input = input[0].toUpperCase() + input.slice(1);
        this.pokemon.name=input;
        this.pokemon.id=response[0].data.id;
        this.pokemon.abilities=response[0].data.abilities;
        this.pokemon.picture=response[0].data.sprites.front_default;
        this.pokemon.type=response[0].data.types[0].type.name;
        this.pokemon.habitat=response[1].data.habitat.name;
        this.pokemon.colour=response[1].data.color.name;
        this.content=true;
      }

      )
    }
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  text-align: center;
  min-height: 140vh;
  background-color: #282c34;
  height: 100%;
  width: 100%;
}
.App-header {
  margin-bottom: 10px;
  padding-top: 5px;
  font-size: calc(10px + 2vmin);
  color: white;
  text-align: center;
}
</style>
