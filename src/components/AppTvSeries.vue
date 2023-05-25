<script>
export default {
    props: {
        name: String,
        original_name: String,
        original_language: String,
        vote_average: Number,
    },
};
</script>

<template>
    <div class="serieTv">
        <div>
            <p>{{ name }}</p>
        </div>
        <div>
            {{ original_name }}
        </div>
        <div>
            {{ original_language }}
        </div>
        <div>
            {{ vote_average }}
        </div>
    </div>
</template>


<style lang="scss" scoped>
.serieTv {
    border: 1px solid black;
}
</style>