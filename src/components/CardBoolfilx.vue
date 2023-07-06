<script>
export default {
    props: {
        title: String,
        originalTitle: String,
        Languages: String,
        vote: Number,
        posterPath: String,
        context: String
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
    <div class="container text-center p-0">
        <ul v-if="posterPath" class="p-0">
            <li id="content" class="list-unstyled">
                <p>Titolo:</p>
                <h5>{{ title }}</h5>
                <p v-if="title !== originalTitle" class="font-min">{{ originalTitle }}</p>
                <p>Lingua:</p>
                <h6 v-if="!hasFlag(Languages)">{{ Languages }}</h6>
                <p><img class="flags mt-3" v-if="hasFlag(Languages)" :src="`/src/assets/img/img/${Languages}.png`" alt="">
                </p>
                <p>Voto:</p>
                <p v-for="star in getStarVote()" :class="star ? 'fas fa-star fa-beat' : 'far fa-star'"></p>
                <p>Trama:</p>
                <p v-if="context" class="text-truncate text-context">{{ context }}</p>
                <p v-else>No trama</p>
            </li>
            <li id="poster-image" class="list-unstyled">
                <img class="poster" :src="getImageUrl(posterPath)" alt="">
            </li>
        </ul>
        <p class="extra" v-else>Nessun elemento</p>
    </div>
</template>
<style scoped>
.flags {
    max-width: 30px;
    max-height: 20px;
    margin-bottom: 10px;
}

.poster {
    max-width: 350px;
    max-height: 350px;
}

#content {
    color: white;
    position: absolute;
    top: 50%;
    right: 0%;
    left: 0%;
    transform: translateY(-50%);
    display: none;

}

ul:hover #content {
    display: block;
}

ul:hover #poster-image {
    opacity: 0.1;
    cursor: pointer;
}

ul {
    position: relative;
}

.fas {
    color: gold;
}

.font-min {
    font-size: 0.7rem;
}

h5 {
    font-size: 0.9rem;
}

.text-context {
    font-size: 0.8rem;
    padding-left: 5px;
    font-weight: bolder;
}

.extra {
    color: white;
    font-weight: bolder;
    margin-top: 150px;
}

p {
    margin-bottom: 9px;
    font-weight: bolder;
}
</style>