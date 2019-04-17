<template>
    <div class="container-fluid">
        <div class="row">
            <button class="btn btn-secondary"
                @click="back">Back to main</button>
        </div>
        <div class="row">
            <div class="col-6 col-sm-4 py-3" v-for="donut in donutList">
                <cmp-donut :donut="donut" :key="donut.id" :order="order"
                    @click.native="add(donut)"
                    style="cursor: pointer"></cmp-donut>
            </div>

        </div>
    </div>
    
</template>

<script>
import Donut from './Donut.vue'
export default {
    props: ['order', 'selectedCategory'],
    data: function() {
        return {
            donutList: [
                {id: '3-0', name: 'Honey Cruller', price: 1.15, img: '../../img/donut_honey.png'},
                {id: '3-1', name: 'Sour Cream Glazed', price: 1.15, img: '../../img/donut_old_glazed.png'},
                {id: '3-2', name: 'Boston Cream', price: 1.15, img: '../../img/donut_boston.png'},
                {id: '3-3', name: 'Canadian Maple', price: 1.15, img: '../../img/donut_maple.png'},
                {id: '3-4', name: 'Chocolate Dip', price: 1.15, img: '../../img/donut_chocolate_dip.png'},
                {id: '3-5', name: 'Vanilla Dip', price: 1.15, img: '../../img/donut_vanilla.png'},
                {id: '3-6', name: 'Apple Fritter', price: 1.15, img: '../../img/donut_apple.png'},
                {id: '3-7', name: 'Honey Dip', price: 1.15, img: '../../img/donut_honey.png'},
                {id: '3-8', name: 'Dutchie', price: 1.15, img: '../../img/donut_dutchie.png'},
                {id: '3-9', name: 'Old-Fashioned', price: 1.15, img: '../../img/donut_old_plain.png'}
                

            ]
        }
    },
    methods: {
        add(theDonut) {
            console.log('add');
            let oldIndexOfNewItem = this.order.findIndex(x => x.id == theDonut.id);
            if (oldIndexOfNewItem == -1) {
                this.order.push({id: theDonut.id, name: theDonut.name, price: theDonut.price, amount: 1});
            } else {
                this.order[oldIndexOfNewItem].amount++;
            }
            
        },
        back() {
            this.$emit('back');
        }
    },
    components: {
        cmpDonut: Donut
    }
}
</script>
