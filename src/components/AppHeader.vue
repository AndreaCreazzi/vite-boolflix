<script>
export default {
    data() {
        return {
            selectFilter: ""
        }
    },
    // emits send to App.vue
    emits: ["term-change", "form-submit"]
}
</script>

<template>
    <nav class="py-3">
        <div class="container">
            <div class="row">
                <!-- Title page -->
                <div class="col-6 d-flex align-items-center">
                    <h1>BOOLFLIX</h1>
                </div>
                <!-- Searchbar -->
                <div class="col-6 d-flex align-items-center">
                    <form class="input-group justify-content-end" @submit.prevent="$emit('form-submit')">
                        <input v-model.trim="selectFilter" @keyup="$emit('term-change', selectFilter)" type="text"
                            placeholder="Film oppure Serie TV">
                        <button class="btn btn-secondary" type="submit">Cerca</button>
                    </form>
                </div>
            </div>
        </div>
    </nav>
</template>

<style scoped>
nav {
    height: 105px;
    background-color: black;
}

.col-6 {
    height: 80px
}

h1 {
    color: red;
}

button {
    border-radius: 50px;
}
</style>