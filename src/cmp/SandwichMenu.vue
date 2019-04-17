<template>
    <div class="container-fluid">
        <div class="row">
            <button class="btn btn-secondary"
                @click="back">Back to main</button>
        </div>
        <div class="row">
            <div class="col-6 col-sm-4 py-3" v-for="sandwich in sandwichList">
                <cmp-sandwich :sandwich="sandwich" :key="sandwich.id" :order="order"
                    @click.native="add(sandwich)"
                    style="cursor: pointer"></cmp-sandwich>
            </div>

        </div>
    </div>
    
</template>

<script>
import Sandwich from './Sandwich.vue'
export default {
    props: ['order', 'selectedCategory'],
    data: function() {
        return {
            sandwichList: [
                {id: '5-0', name: 'Turkey Bacon Club Sandwich', price: 1.15, img: '../../img/sandwich_turkey.png'},
                {id: '5-1', name: 'Ham & Cheddar Sandwich', price: 1.15, img: '../../img/sandwich_ham.png'},
                {id: '5-2', name: 'B.L.T. Sandwich', price: 1.15, img: '../../img/sandwich_blt.png'},
                {id: '5-3', name: 'Artisan-Style Grilled Cheese Sandwich', price: 1.15, img: '../../img/sandwich_grilled.png'},
                {id: '5-4', name: 'Chicken Salad Sandwich', price: 1.15, img: '../../img/sandwich_chicken.png'}
                

            ]
        }
    },
    methods: {
        add(theSandwich) {
            console.log('add');
            let oldIndexOfNewItem = this.order.findIndex(x => x.id == theSandwich.id);
            if (oldIndexOfNewItem == -1) {
                this.order.push({id: theSandwich.id, name: theSandwich.name, price: theSandwich.price, amount: 1});
            } else {
                this.order[oldIndexOfNewItem].amount++;
            }
            
        },
        back() {
            this.$emit('back');
        }
    },
    components: {
        cmpSandwich: Sandwich
    }
}
</script>
