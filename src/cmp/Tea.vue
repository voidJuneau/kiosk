<template>
    <div class="card h-100">
        <div class="card-body d-flex align-items-center">
            <img v-bind:src="tea.img" alt="coffee.name" class="img-fluid mx-auto">
        </div>
        <div class="card-footer p-0">
            {{ tea.name }} {{ tea.price }}
        </div>
    </div>
</template>

<script>

export default {
    props: ['order', 'tea'],
    methods: {
    }
}
</script>

<style>
</style>

