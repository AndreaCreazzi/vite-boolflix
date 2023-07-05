<script>
export default {
    props: {
        title: String,
        originalTitle: String,
        Languages: String,
        vote: Number,
        posterPath: String
    },
    data() {
        return {}
    },
    methods: {
        hasFlag(language) {
            return ['it', 'en'].includes(language);
        },
        getImageUrl(posterPath) {
            const baseUrl = 'https://image.tmdb.org/t/p/';
            const imageSize = 'w342'; // Dimensione desiderata dell'immagine
            return `${baseUrl}${imageSize}${posterPath}`;
        }
    }
}
</script>
<template>
    <div class="container text-center">
        <ul>
            <li class="list-unstyled">
                <h4>{{ title }}</h4>
                <p>{{ originalTitle }}</p>
                <h6 v-if="!hasFlag(Languages)">{{ Languages }}</h6>
                <img class="flags" v-if="hasFlag(Languages)" :src="`/src/assets/img/img/${Languages}.png`" alt="">
                <p>{{ vote }}</p>
                <img class="poster" v-if="posterPath" :src="getImageUrl(posterPath)" alt="">
            </li>
        </ul>
    </div>
</template>
<style>
.flags {
    max-width: 30px;
    max-height: 20px;
    margin-bottom: 10px;
}

.poster {
    max-width: 100px;
    max-height: 100px;
}
</style>