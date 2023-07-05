<script>
export default {
    data() {
        return {}
    }
}
</script>

<template>
    <nav class="container-fluid">
        <div class="row">
            <div class="col-6 d-flex align-items-center">
                <h1>Boolflix</h1>
            </div>
            <div class="col-6 d-flex align-items-center">
                <div class="input-group justify-content-end">
                    <input class="me-2" type="text" placeholder="Film oppure Serie TV">
                    <button class="btn btn-secondary" type="button">Cerca</button>
                </div>
            </div>
        </div>
    </nav>
</template>

<style scoped>
nav {
    background-color: black;
}

.col-6 {
    height: 80px
}

h1 {
    color: red;
}
</style>