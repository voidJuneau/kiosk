<template>
    <div class="card h-100">
        <div class="card-body d-flex align-items-center">
            <img v-bind:src="sandwich.img" alt="sandwich.name" class="img-fluid mx-auto">
        </div>
        <div class="card-footer p-0">
            {{ sandwich.name }} {{ sandwich.price }}
        </div>
    </div>
</template>

<script>
export default {
    props: ['order', 'sandwich'],
    methods: {
    }
}
</script>

<style>
</style>

