<template>
    <div class="card h-100">
        <div class="card-body d-flex align-items-center size">
            <br><br>
            <p class="fluid mx-auto">{{ size.initial }}</p>
            <br>
        </div>
    </div>
</template>

<script>
export default {
    props: ['size'],
    data: function() {
        return {
            
        }
    }
}
</script>