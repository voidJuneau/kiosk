<template>
     <div class="card h-100">
        <div class="card-body d-flex align-items-center">
            <img v-bind:src="cold.img" alt="cold.name" class="img-fluid mx-auto">
        </div>
        <div class="card-footer p-0">
            {{ cold.name }} {{ cold.price }}
        </div>
    </div>
</template>

<script>

export default {
    props: ['order', 'cold'],
    methods: {
    }
}
</script>

<style>
</style>

