<template>
  <div>
    <h1>¿Quién es este Pokémon?</h1>
    <PokemonPicture :pokemonId="59" :showPokemon="true" />
    <PokemonOptions :pokemons="pokemonsArr" />
  </div>
</template>

<script>
import PokemonPicture from "@/components/PokemonPicture.vue";
import PokemonOptions from "@/components/PokemonOptions.vue";
import { getPokemonOptions } from "@/herlpers/getPokemonOptions.js";


// console.log(getPokemonOptions())

export default {
  components: { PokemonPicture, PokemonOptions },
  data() {
    return {
      pokemonsArr: [], 
    };
  },
  methods:{
    async mixPokemonArray() {
      this.pokemonsArr = await getPokemonOptions()
      console.log(this.pokemonsArr)
    }
  },
  mounted() {
    this.mixPokemonArray()
  }
};
</script>

