<template>
    <cmp-size
                v-for="(size, index) in sizeOption" :size="size" :key="index"
                @click.native="passAddInfo(size, index)"
                style="cursor: pointer"
                class="col-6 col-sm-3"></cmp-size>
</template>

<script>
import Size from './Size.vue'
export default {
    data: function() {
        return {
            sizeOption: [
                {name: 'Small', initial: 'SM'}, 
                {name: 'Medium', initial: 'M'}, 
                {name: 'Large', initial: 'L'}, 
                {name: 'Extra Large', initial: "XL"}
            ]
        }
    },
    methods: {
        passAddInfo(size, index) {
            this.$emit('info', size.name, index);
        }
    }
}
</script>