<template>
  <b-container class="p-3 bg-secondary home-view rounded">
    <b-row>
      <div id="blue-ball" class="bg-primary rounded-circle m-4" />
      <div class="tiny-balls bg-danger rounded-circle mr-1 mt-4" />
      <div class="tiny-balls bg-warning rounded-circle mr-1 mt-4" />
      <div class="tiny-balls bg-success rounded-circle mr-1 mt-4" />
    </b-row>
    <b-row>
      <h1 v-if="fire" class="fire">Flareon is a fire Pokémon</h1>
      <h1 v-else-if="water" class="water">Horea is a water Pokémon</h1>
      <h1 v-else-if="grass" class="grass">Bellosom is a grass Pokémon</h1>
      <h1 v-else>No type specified</h1>
      <h1 v-show="fire">Visible in the DOM, but invisible to the eye</h1>
    </b-row>
    <ul>
      <li v-for="detail in details" :key="detail.index">
        {{ detail }}
      </li>
    </ul>
    <div v-for="pokemon in pokemons" :key="pokemon.index">
      <h3>{{ pokemon.name }}</h3>
      <p>{{ pokemon.type }}</p>
    </div>

    <p :id="name">Hellow {{ firstName }}</p>
    <button v-on:click="aClickHandler('hellow')">my ugly button</button>
    <button
      type="submit"
      @click.prevent="aClickHandler('whow thats alert ' + firstName)"
    >
      Hellow
    </button>

    <form @submit="formSubmit">
      <input v-model="searchQuery" />
      <button type="submit">Search</button>
      <button type="submit" @click.prevent="resetForm">reset</button>
    </form>

    <div :class="{darkTheme: isDark}">
      <h2
        v-for="pokemon in pokemons"
        :key="pokemon.index"
        :class="pokemon.color"
      >
        {{ pokemon.name }}
      </h2>
    </div>
    <button @click="isDark = !isDark">Enter Darkness</button>

    <h2>
      {{title}}
    </h2>

    <h2 v-for="pokemon in fieryPokemons" :key="pokemon.index">
      {{ pokemon }}
    </h2>

    
    <b-row> </b-row>

    <Pokemon :pokemons="starters" />
  </b-container>
</template>

<script>

import Pokemon from "../components/Pokemon";

export default {
  name: "Home",
  components: {
    Pokemon
  },
  data() {
    return {
      firstName: "Burak",
      fire: false,
      water: false,
      grass: true,
      details: ["awesome", "fire", "dragon"],
      pokemons: [
        { name: "charmender", type: "fire", color: "red" },
        { name: "squirtle", type: "water", color: "blue" },
        { name: "bulbasaur", type: "grass", color: "green" },
      ],
      pokemonss: ["charmander", "squirtle", "bulbasaur"],
      poke: {
        name: "bulbasaur",
        number: "001"
      },
      checked: true,
      isDark: false,
      searchQuery: "",
      starters: [
        { name: "charmander", type: "fire" },
        { name: "squirtle", type: "water" },
        { name: "bulbasaur", type: "grass" },
      ]
    };
  },
  methods: {
    resetForm() {
      this.searchQuery = "";
    },
    formSubmit() {
      alert(`hi you want to search for: ${this.searchQuery}`);
    },
    isFiery(value){
      return value.includes("bulb")
    }
  },
  computed: {
    title(){
      return this.poke.name + " " + this.poke.number
    },
    fieryPokemons() {
      return this.pokemonss.filter(this.isFiery)
    }
  }
};
</script>

<style lang="scss">
.darkTheme{
  background-color: black;

  h2{
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
