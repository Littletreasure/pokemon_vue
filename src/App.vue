<template>
  <div id="app">
    <header class="App-header">
          <h1>Pokemon</h1>
    </header>
    <search v-on:search="getPokemon($event)" />
  </div>
</template>

<script>
import search from './components/search.vue';

export default {
  name: 'App',
  components: {
    'search': search
  },
  data() {
    return {
     
    }
    
  },
  methods: {
    getPokemon: function(pokemon) {
      console.log(pokemon)
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
