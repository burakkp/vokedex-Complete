<template>
  <b-container class="p-3 the-blue home-view rounded">
    <b-row>
        Welcome to about page {{ $route.params.name }}
    </b-row>
    <router-link to="/">home</router-link>
  </b-container>
</template>

<script>

export default {
  name: "About",
  data() {
    return {};
  },
  mounted(){
      console.log('data: ', this.$route.params.name)
  }
};
</script>

<style lang="scss">
.the-blue{
    background-color: blue;
}
</style>
