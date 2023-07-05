<script>
export default {
    props: {
        title: String,
        originalTitle: String,
        Languages: String,
        vote: Number
    },
    data() {
        return
    }
}
</script>
<template>
    <div class="container text-center">
        <ul>
            <li class="list-unstyled">
                <h4>{{ title }}</h4>
                <p>{{ originalTitle }}</p>
                <h6 v-if="Languages !== 'it' && 'en'">{{ Languages }}</h6>
                <img :src="`/src/assets/img/img/${Languages}.png`" alt="">
                <p>{{ vote }}</p>
            </li>
        </ul>
    </div>
</template>
<style>
img {
    max-width: 30px;
    max-height: 20px;
    margin-bottom: 10px;
}
</style>