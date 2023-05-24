<script>

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';
import { store } from './store';

export default {

  data() {
    return {
      store,
    };
  },

  components: {
    AppHeader,
    AppMain,
  },

  methods: {
    searchFind() {
      console.log(store.searchBar)
    },

    RequestMoviesFromApi() {
      axios
        .get('https://api.themoviedb.org/3/search/movie?api_key=21df2f399925b36ce74442455c67fc8a&query=all',)
        .then(response => (this.store.movieList = response.data.results));
    }
  },
}





</script>

<template>
  <AppHeader @performSearch="searchFind" />
  <AppMain />
</template>

<style lang="scss" scoped></style>
