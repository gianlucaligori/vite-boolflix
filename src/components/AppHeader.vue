<script>
import { store } from "../store";

export default {
    data() {
        return {
            store,
        };
    },

    methods: {
        emitSearchBar() {
            this.$emit('searchPerformed');
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
                <input type="text" placeholder="Cerca Film o SerieTV" v-model="store.SearchBar"
                    @keyup.enter="emitSearchBar" />

                <button>CERCA</button>
            </div>
        </nav>
    </header>
</template>

<style lang="scss" scoped>
.flex_container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 5rem;
    padding-inline: 2rem;
    background-color: black;

    h1 {
        color: red;
    }

    .search {
        input {
            margin-right: 1rem;
        }
    }
}
</style>