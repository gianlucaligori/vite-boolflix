<script>
import { store } from "../store";
import AppMovies from "./AppMovies.vue";
import AppTvSeries from "./AppTvSeries.vue";

export default {
    data() {
        return {
            store,
        };
    },

    components: {
        AppMovies,
        AppTvSeries,
    },
};
</script>

<template>
    <div class="main_container">

        <div class="movies">
            <AppMovies v-for="movies in store.ArrMovies" :key="movies.id" :poster_path="movies.poster_path"
                :title="movies.title" :original_title="movies.original_title" :original_language="movies.original_language"
                :vote_average="movies.vote_average" />
        </div>

        <div class="series">
            <AppTvSeries v-for="series in store.ArrTvSeries" :key="series.id" :poster_path="series.poster_path"
                :name="series.name" :original_name="series.original_name" :original_language="series.original_language"
                :vote_average="series.vote_average" />
        </div>

    </div>
</template>

<style lang="scss" scoped>
.main_container {
    display: flex;
    color: antiquewhite;
    background-color: rgb(36, 36, 36);
    padding-top: 5rem;

}
</style>
