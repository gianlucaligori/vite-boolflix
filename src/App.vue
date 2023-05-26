<script>

import axios from "axios";
import { store } from "./store"

export default {
  data() {
    return {
      store,
    };
  },



  methods: {
    RequestDataFromApi() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "3230330c1c509c72a0be97deca021c40",
            query: this.store.SearchBar,
          },
        })
        .then((response) => (this.store.ArrMovies = response.data.results));

      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "3230330c1c509c72a0be97deca021c40",
            query: this.store.SearchBar,
          },
        })
        .then((response) => (this.store.ArrTvSeries = response.data.results));
    },
  },
};
</script>

<template>
  <header>
    <nav>
      <div>
        <h1>BOOLFLIX</h1>
      </div>

      <div class="search">
        <input type="text" placeholder="Cerca Film o SerieTV" v-model="store.SearchBar" @keyup.enter="emitSearchBar" />
        <button @click="RequestDataFromApi">CERCA</button>
      </div>
    </nav>
  </header>


  <div class="main_container">

    <div class="movie_container">

      <div v-for="(movie, index) in store.ArrMovies" :key="index" class="movie">
        <div>
          <!-- <img src="https://image.tmdb.org/t/p/w342" + movie.poster_path alt=""> -->
          {{ movie.title }}
          {{ movie.overview }}
        </div>
      </div>

    </div>


    <div class="serie_container">

      <div class="series">
        <div v-for="(serie, index) in store.ArrTvSeries" :key="index" class="serieTv">
          <div>
            <span> {{ serie.title }} </span>
            {{ serie.overview }}
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}



nav {
  height: 5rem;
  padding: 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: black;
  color: red;
  margin-bottom: 5rem;

}

.movie_container,
.serie_container {
  max-width: 1300px;
  gap: 4rem;
  display: flex;
  flex-wrap: wrap;
  margin: auto;
}

.movie {
  border: 1px solid black;
  max-height: 400px;
  aspect-ratio: 2 / 3;
}
</style>

