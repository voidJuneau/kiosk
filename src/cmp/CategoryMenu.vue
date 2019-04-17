<template>
    <div class="card h-100">
        <div class="card-body d-flex align-items-center">
            <img v-bind:src="category.img" alt="category.name" class="img-fluid mx-auto">
        </div>
        <div class="card-footer p-0">
            {{ category.name }}
        </div>
    </div>
</template>
<script>
export default {
    props: ['category']
}
</script>
