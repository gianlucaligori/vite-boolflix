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
        name: String,
        original_name: String,
        original_language: String,
        vote_average: Number,
    },
};
</script>

<template>
    <div class="movies">
        <div>
            <img v-if="poster_path" :src="`http://image.tmdb.org/t/p/w342${poster_path}`" alt="">
            <img v-else src="./ assets / img / Non - disponibile - _04.jpg" alt="">
        </div>
        <div>
            <p>{{ name }}</p>
        </div>
        <div>
            {{ original_name }}
        </div>
        <div>
            {{ languageImage(original_language) }}
        </div>
        <div>
            {{ convertiVotiStars(vote_average) }}
        </div>
    </div>
</template>


<style lang="scss" scoped>
.movie_containe {
    gap: 1rem;
    display: flex;
    flex-wrap: wrap;
    margin: auto;
    color: white;
}

.movie {
    padding: 1rem;
    display: flex;
    flex-wrap: wrap;
    margin: auto;
    border: 1px solid black;
}
</style>