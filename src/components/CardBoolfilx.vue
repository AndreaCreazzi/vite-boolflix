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
            const imageSize = 'w342';
            return `${baseUrl}${imageSize}${posterPath}`;
        },
        getStarVote() {
            const roundedVote = Math.ceil(this.vote / 2);
            return Array.from({ length: 5 }, (_, index) => index + 1 <= roundedVote);
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
                <h6 v-if="!hasFlag(Languages)">Lingua: {{ Languages }}</h6>
                <p>Lingua: <img class="flags" v-if="hasFlag(Languages)" :src="`/src/assets/img/img/${Languages}.png`"
                        alt="">
                </p>
                <p v-for="star in getStarVote()" :class="star ? 'fas fa-star' : 'far fa-star'"></p>
                <img class="poster" v-if="posterPath" :src="getImageUrl(posterPath)" alt="">
            </li>
        </ul>
    </div>
</template>
<style scoped>
.flags {
    max-width: 30px;
    max-height: 20px;
    margin-bottom: 10px;
}

.poster {
    max-width: 100px;
    max-height: 100px;
}

.fas {
    color: gold;
}
</style>