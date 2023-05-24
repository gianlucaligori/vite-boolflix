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

        <input type="text" @keyup.enter="$emit('performSearch')" v-model="store.searchBar">
        <button></button>
    </nav>
</template>

<style lang="scss" scoped>
@use '../assets/styles/partials/reset' as *;


nav {
    max-height: 100px;
    border: 1px solid black;
}
</style>
