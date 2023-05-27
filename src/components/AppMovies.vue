<script>
import { store } from '../store';

export default {

    data() {
        return {
            store,
        }
    },

    methods: {
        languageImage(index) {
            if (index == 'en') {
                return 'https://flagsapi.com/GB/flat/32.png'
            } else if (index == 'ja') {
                return 'https://flagsapi.com/JP/flat/32.png'
            } else {
                return ('https://flagsapi.com/' + index.toUpperCase() + '/flat/32.png')
            }
        },


        convertiVotiStars(number) {
            // Trasformazione del numero
            const trasformNumber = Math.floor((number - 1) / 2) + 1;

            // Creazione della recensione
            let review = "";
            for (let i = 1; i <= 5; i++) {
                if (i <= trasformNumber) {
                    review += "★ "; // stella piena
                } else {
                    review += "☆ "; // stella vuota
                }
            }

            return review;
        },
    },


    props: {
        poster_path: String,
        title: String,
        original_title: String,
        original_language: String,
        vote_average: Number,
    },
};
</script>

<template>
    <div class="movies">

        <div class="movie_info">


            <img v-if="poster_path" :src="`http://image.tmdb.org/t/p/w342${poster_path}`" alt="">
            <img v-else src="./ assets / img / Non - disponibile - _04.jpg" alt="">

            <p>{{ title }}</p>
            <p>{{ original_title }}</p>

            <img :src="languageImage(original_language)" alt="">

            <p>{{ convertiVotiStars(vote_average) }}</p>
        </div>

    </div>
</template>


<style lang="scss" scoped>
p {
    padding-top: .7rem;
}

.movies {
    margin-inline: 4rem;
}
</style>