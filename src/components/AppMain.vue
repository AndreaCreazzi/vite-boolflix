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
            <h2 class="p-4">FILM</h2>
            <div class="row g-4 row-cols-3 row-cols-md-4 row-cols-lg-5">
                <div class="col" v-for="item in store.film" :key="item.id">
                    <CardBoolflix :title="item.title" :originalTitle="item.original_title"
                        :Languages="item.original_language" :vote="item.vote_average" />
                </div>
            </div>
        </div>
        <div class="container py-5">
            <h2 class="p-4">SERIE TV</h2>
            <div class="row g-4 row-cols-3 row-cols-md-4 row-cols-lg-5">
                <div class="col" v-for="item in store.tv" :key="item.id">
                    <CardBoolflix :title="item.name" :originalTitle="item.original_name" :Languages="item.original_language"
                        :vote="item.vote_average" />
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
section {
    height: 100vh;
}

.overflow {
    overflow: auto;
}
</style>