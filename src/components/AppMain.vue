<script>
import { store } from '../data/store';
import CardBoolflix from '../components/CardBoolfilx.vue'
export default {
    components: { CardBoolflix },
    data() {
        return { store }
    }
}
</script>

<template>
    <section class="overflow">
        <div class="container py-5">
            <h2 class="text-center" v-if="!store.film.length || !store.tv.length">INIZIA CERCANDO QUALCOSA <i
                    class="fa-solid fa-arrow-turn-up"></i></h2>
            <h2 class="text-center" v-if="!store.film.length || !store.tv.length">I MIGLIORI FILM O SERIE TV LI TROVI SOLO
                QUI <i class="fa-solid fa-clapperboard"></i></h2>
            <h2 v-if="store.film.length" class="p-4">FILM</h2>
            <div class="row g-4 row-cols-3 row-cols-md-4 row-cols-lg-5">
                <div class="col" v-for="item in store.film" :key="item.id">
                    <CardBoolflix :title="item.title" :originalTitle="item.original_title"
                        :Languages="item.original_language" :vote="item.vote_average" :posterPath="item.poster_path"
                        :context="item.overview" />
                </div>
            </div>
        </div>
        <div class="container py-5">
            <h2 v-if="store.tv.length" class="p-4">SERIE TV</h2>
            <div class="row g-4 row-cols-3 row-cols-md-4 row-cols-lg-5">
                <div class="col" v-for="item in store.tv" :key="item.id">
                    <CardBoolflix :title="item.name" :originalTitle="item.original_name" :Languages="item.original_language"
                        :vote="item.vote_average" :posterPath="item.poster_path" :context="item.overview" />
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
section {
    background-color: #434343;
    height: 100vh;
}

.overflow {
    overflow: auto;
}

h2 {
    color: red;
}
</style>