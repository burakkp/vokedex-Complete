<template>
  <b-col>
    <h3>SEARCH RESULTS FOR {{ query }}</h3>
  </b-col>
</template>

<script>
export default {
  name: "PokemonDetails",
  props: {
      query: String
  },
  data() {
    return {};
  },
};
</script>

<style>
</style>