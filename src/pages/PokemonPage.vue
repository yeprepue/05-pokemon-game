<template>
        <div>
          <h1>¿Quién es este Pokémon?</h1>
          <PokemonPicture :pokemonId="649" :showPokemon="true" />
          <PokemonOptions />
        </div>
      </template>
      
      <script>
      import PokemonPicture from '@/components/PokemonPicture';
      import PokemonOptions from '@/components/PokemonOptions';
      import getPokemons from '@/helpers/getPokemons';
      
      console.log(getPokemons());
      export default {
        components: {
          PokemonPicture,
          PokemonOptions
        }
      }
      </script>
      vgy u9op{
        dfgk._
      }