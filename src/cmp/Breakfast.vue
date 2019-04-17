<template>
    <div class="card h-100">
        <div class="card-body d-flex align-items-center">
            <img v-bind:src="breakfast.img" alt="breakfast.name" class="img-fluid mx-auto">
        </div>
        <div class="card-footer p-0">
            {{ breakfast.name }} {{ breakfast.price }}
        </div>
    </div>
</template>

<script>
export default {
    props: ['order', 'breakfast'],
    methods: {
    }
}
</script>

<style>
</style>

