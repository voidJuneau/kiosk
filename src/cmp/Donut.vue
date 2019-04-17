<template>
    <div class="card h-100">
        <div class="card-body d-flex align-items-center">
            <img v-bind:src="donut.img" alt="donut.name" class="img-fluid mx-auto">
        </div>
        <div class="card-footer p-0">
            {{ donut.name }} {{ donut.price }}
        </div>
    </div>
</template>

<script>
export default {
    props: ['order', 'donut'],
    methods: {
    }
}
</script>

<style>
</style>

