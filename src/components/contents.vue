<template>
  <main class="main">
   <div class="content">
    <h1>{{pokemon.name}}</h1>
    <img v-bind:src="pokemon.picture" v-bind:alt="pokemon.name" width="200" />
    <div class="type">
      <p>Type: {{pokemon.type}}</p>
      <p>Pokemon ID: {{pokemon.id}}</p>
    </div>
    <div class="type">
      <p>Habitat: {{pokemon.habitat}}</p>
      <p>Colour: {{pokemon.colour}}</p>
    </div>
    <p>{{pokemon.name}}'s abilities are:</p>
    <ul>
<li v-for="ability in pokemon.abilities" v-bind:key="ability.ability.slot">- {{ability.ability.name}}</li>
    </ul>
    </div>
  </main>
</template>

<script>
export default {
  props: ['pokemon'],

  data() {
    return {
     
    }
    
  },
 
}
</script>

<style>
.main {
  
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
}
.content {
  margin-top: 20px;
  border-radius: 30px;
  border-style: solid;
  padding-bottom: 20px;
  width: 40%;
  background-color: rgb(88, 86, 86);
}
.type {
  display: grid;
  grid-template-columns: 1fr 1fr;
  justify-content: space-around;
  margin-right: 10px;
}
ul {
  display: flex;
  flex-direction: column;
  list-style-type: none;
  padding: 0;
}
</style>