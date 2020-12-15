<template>
  <div id="search">
    <form>
          <label>Please enter a Pokemon name:</label>
            <input type="text" v-model="pokemon" />
            <button v-on:click.prevent="$emit('search', pokemon)">Pick me!</button>
    </form>
  </div>
</template>

<script>


export default {
  
  data() {
    return {
     pokemon: ''
    }
    
  },
  
}
</script>

<style>
#search {
  margin: 20px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  font-size: calc(10px + 2vmin);
  color: white;
  text-align: left;
}
label {
  margin-right: 10px;
}
button {
  margin-left: 10px;
}
</style>