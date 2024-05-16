<template>
  <h1 v-if="!pokemon">Espere por favor......</h1>

  <div v-else>
    <h1>¿Quién es este Pokémon?</h1>
    <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon" />
    <PokemonOptions :pokemons="pokemonsArr" @selectionPokemon="checkAnswer" />
    <template v-if="showAnswer">
      <h2>{{ message }}</h2>
      <button @click="newGame()">Nuevo Juego</button>
    </template>
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
      pokemon: null,
      showPokemon: false,
      showAnswer: false,
      message: "",
    };
  },
  methods: {
    async mixPokemonArray() {
      this.pokemonsArr = await getPokemonOptions();

      const rndInt = Math.floor(Math.random() * 4);
      this.pokemon = this.pokemonsArr[rndInt];
    },
    checkAnswer(selectedId) {
      this.showPokemon = true;
      this.showAnswer = true;
      if (selectedId === this.pokemon.id) {
        this.message = `Correcto, ${this.pokemon.name} `;
      } else {
        this.message = `Oops, era ${this.pokemon.name} !!!!`;
      }
    },
    newGame() {
      this.showPokemon = false;
      this.showAnswer = false;
      this.pokemonsArr = [];
      this.mixPokemonArray();
    },
  },
  mounted() {
    this.mixPokemonArray();
  },
};
</script>
