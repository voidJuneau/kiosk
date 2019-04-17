<template>
    <div class="container-fluid">
        <div class="row">
            <button class="btn btn-secondary"
                @click="back">Back to main</button>
        </div>
        <div class="row">
            <div class="col-6 col-sm-4 py-3" v-for="breakfast in breakfastList">
                <cmp-breakfast :breakfast="breakfast" :key="breakfast.id" :order="order"
                    @click.native="add(breakfast)"
                    style="cursor: pointer"></cmp-breakfast>
            </div>
        </div>
    </div>
    
</template>

<script>
import Breakfast from './Breakfast.vue'
export default {
    props: ['order', 'selectedCategory'],
    data: function() {
        return {
            breakfastList: [
                {id: '4-0', name: 'Hot Breakfest Sandwich', price: 3.99, img: '../../img/breakfast_sandwich.png'},
                {id: '4-1', name: 'Bagel B.E.L.T.', price: 3.99, img: '../../img/breakfast_bagel.png'},
                {id: '4-2', name: 'Fresh Grilled Breakfest Wraps', price: 3.99, img: '../../img/breakfast_wraps.png'},
                {id: '4-3', name: 'Homestyle Oatmeal', price: 2.49, img: '../../img/breakfast_oatmeal.png'},
                {id: '4-4', name: 'Hash Brown', price: 0.99, img: '../../img/breakfast_hash.png'},
                {id: '4-5', name: 'Breakfest Snacks', price: 2.99, img: '../../img/breakfast_snacks.png'}
                

            ]
        }
    },
    methods: {
        add(theBreakfast) {
            console.log('add');
            let oldIndexOfNewItem = this.order.findIndex(x => x.id == theBreakfast.id);
            if (oldIndexOfNewItem == -1) {
                this.order.push({id: theBreakfast.id, name: theBreakfast.name, price: theBreakfast.price, amount: 1});
            } else {
                this.order[oldIndexOfNewItem].amount++;
            }
            
        },
        back() {
            this.$emit('back');
        }
    },
    components: {
        cmpBreakfast: Breakfast
    }
}
</script>
