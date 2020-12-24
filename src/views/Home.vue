<template>
  <b-container class="p-3 bg-secondary home-view rounded">
    <b-row>
      <div id="blue-ball" class="bg-primary rounded-circle m-4" />
      <div class="tiny-balls bg-danger rounded-circle mr-1 mt-4" />
      <div class="tiny-balls bg-warning rounded-circle mr-1 mt-4" />
      <div class="tiny-balls bg-success rounded-circle mr-1 mt-4" />
    </b-row>
    <b-row class="p-5">
      <PokemonImg />
      <SearchPokemon @new-search-query="handleQuery" />
    </b-row>
    <b-row class="p-5">
      <PokemonDetails />
      <SearchResult :query="query" />
    </b-row>
  </b-container>
</template>

<script>
import PokemonDetails from "../components/PokemonDetails";
import PokemonImg from "../components/PokemonImg";
import SearchPokemon from "../components/SearchPokemon";
import SearchResult from "../components/SearchResult";

export default {
  name: "Home",
  components: {
    PokemonDetails,
    PokemonImg,
    SearchPokemon,
    SearchResult,
  },
  data() {
    return {
      query: "",
    };
  },
  methods: {
    handleQuery(data){
      this.query = data
    }
  },
  computed: {
    title() {
      return this.poke.name + " " + this.poke.number;
    },
    fieryPokemons() {
      return this.pokemonss.filter(this.isFiery);
    },
  },
};
</script>

<style lang="scss">
.darkTheme {
  background-color: black;

  h2 {
    color: black;
  }
}
.fire {
  color: red;
}
.water {
  color: blue;
}
.grass {
  color: green;
}
.red {
  color: red;
}
.blue {
  color: blue;
}
.green {
  color: green;
}
#blue-ball {
  height: 70px;
  width: 70px;
  border: 10px solid lightgrey;
}

.tiny-balls {
  height: 20px;
  width: 20px;
  border: 1px solid black;
}

.home-view {
  border: 3px solid black;
}
</style>
