<template>
  <div id="pokemon">
    <div v-for="pokemon in pokemons" :key="pokemon.index">
      <h2>Name: {{ pokemon.name }}</h2>
      <p>type: {{ pokemon.type }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "pokemon",
  props: {
    pokemons: {
      type: Array,
      default: () => {
        return { name: "", type: "" };
      },
    },
  },
  data() {
    return {};
  },
};
</script>
