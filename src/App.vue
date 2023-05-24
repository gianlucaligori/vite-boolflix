<script>

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';
import { store } from '../src/store';

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

  created() {
    // qui fare la richiesta all'api
    axios
      .get('https://api.themoviedb.org/3/search/movie?api_key=3230330c1c509c72a0be97deca021c40&query=Jack+Reacher')
    // .then(response => (this.store.cardList = response.data.data));			
  },
}





</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style lang="scss" scoped></style>
