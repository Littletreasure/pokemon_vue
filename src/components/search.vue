<template>
  <div id="search">
    <form>
          <label>Please enter a Pokemon name:</label>
            <input type="text" v-model="pokemon" />
            <button v-on:click.prevent="search">Pick me!</button>
    </form>
    <button v-on:click.prevent="reset">Reset</button>
  </div>
</template>

<script>


export default {
  
  data() {
    return {
     pokemon: ''
    }
    
  },
 methods: {
   search: function() {
     this.$emit('search', this.pokemon);
     this.pokemon=''
   },
   reset: function() {
     this.$emit('reset');
   }
 }
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