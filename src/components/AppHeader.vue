<script>
import { store } from '../store'

export default {
    data() {
        return {
            store,
        }
    },
    methods: {
    },
};
</script>

<template>
    <nav>
        <h1>Boolean Streaming</h1>

        <div class="btns">
            <input type="text" @keyup.enter="$emit('performSearch')" v-model="store.searchBar">
            <button>Cerca</button>
        </div>
    </nav>
</template>

<style lang="scss" scoped>
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

nav {
    display: flex;
    justify-content: space-around;
    align-items: center;
    height: 4rem;
    background-color: black;
    color: white;
}
</style>
