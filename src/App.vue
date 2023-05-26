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
    languageImage(index) {
      if (index == 'en') {
        return 'https://flagsapi.com/GB/flat/32.png'
      } else if (index == 'ja') {
        return 'https://flagsapi.com/JP/flat/32.png'
      } else {
        return ('https://flagsapi.com/' + index.toUpperCase() + '/flat/32.png')
      }
    },

    convertToStars(voto) {
      let votoArrotondato = Math.round(voto / 2); // Arrotonda il voto a interi da 1 a 5
      let stelle = '★'.repeat(votoArrotondato) + '☆'.repeat(5 - votoArrotondato); // Costruisce la stringa con stelle e stelle vuote
      return stelle;
    }



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

  <!-- QUI CONTAINER GENERALE CONTENUTI -->

  <div class="main_container">


    <!-- QUI CONTAINER SERIE TV -->

    <div class="movie_container">
      <div v-for="(movie, index) in store.ArrMovies" :key="index" class="movie">
        <div>
          <div>
            <img v-if="movie.poster_path" :src="`http://image.tmdb.org/t/p/w342${movie.poster_path}`" alt="">
            <img v-else src="./ assets / img / Non - disponibile - _04.jpg" alt="">


            <h3>
              {{ movie.title }}
            </h3>
          </div>

          <div>
            <h5>{{ movie.original_title }}</h5>
          </div>

          <div>
            <span>
              <img :src="languageImage(movie.original_language)" alt="">

            </span>
          </div>

          <div>
            <p> {{ convertToStars(movie.vote_average) }}</p>
          </div>
        </div>
      </div>

    </div>

    <!-- QUI CONTAINER SERIE TV -->


    <div class="serie_container">
      <div v-for="(serie, index) in store.ArrTvSeries" :key="index" class="tvseries">
        <div class="card">

          <img v-if="serie.poster_path" :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`" alt="">
          <img v-else src="./ assets / img / Non - disponibile - _04.jpg" alt="">

          <h3>
            {{ serie.name }}
          </h3>

          <h5>
            {{ serie.name }}
          </h5>


          <div>
            <img :src="languageImage(serie.original_language)" alt="">
          </div>

          <p> {{ convertToStars(serie.vote_average) }}</p>

        </div>
      </div>

    </div>

    <!-- QUI CONTAINER SERIE TV -->
  </div>
</template>





<!-- INIZIO STILE  -->
<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main_container {
  background-color: rgb(36, 36, 36);
  padding-top: 5rem;

}

nav {
  height: 7rem;
  padding: 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: black;
  color: red;
}

.movie_container,
.serie_container {
  gap: 1rem;
  display: flex;
  flex-wrap: wrap;
  margin: auto;
  color: white;
}

.movie,
.tvseries {
  padding: 1rem;
  display: flex;
  flex-wrap: wrap;
  margin: auto;
  border: 1px solid black;
}
</style>

