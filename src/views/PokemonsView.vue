<template>
 <div class="Pokemons">   
  <h1>Pokemons</h1>
     <ul>
        <li v-for="poke in pokemons">
          <router-link :to="`/pokemons/${poke.name}`">{{
            poke.name
            }}</router-link>
        </li>
        
     </ul>
</div>
</template>

<script setup>
import axios from 'axios';
import { ref } from 'vue';


const pokemons = ref([])

const getData = async () => {
    try {
     const {data} =  await axios.get('https://pokeapi.co/api/v2/pokemon');
        pokemons.value = data.results
    } catch (error){
        console.log(error)
        
    }
};

getData();

</script>

<style>

</style> 