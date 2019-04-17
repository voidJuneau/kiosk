<template>
    <div class="container-fluid">
        <div class="row" v-if="!selectedCoffee">
            <button class="btn btn-secondary"
                @click="back">Back to main</button>
        </div>
        <div class="row" v-if="!selectedCoffee">
            <div class="col-6 col-sm-4 py-3" v-for="coffee in coffeeList">
            <cmp-coffee
                :coffee="coffee" :key="coffee.id" :order="order"
                @click.native="selectedCoffee = coffee"></cmp-coffee>
            </div>

        </div>
        <div class="row"
            v-if="selectedCoffee">
            <button class="btn btn-secondary"
                @click="selectedCoffee = null">Back to Coffee</button>
        </div>
        <div class="row"
            v-if="selectedCoffee">
            <div class="col-6 col-sm-4 py-3" v-for="(size, index) in sizeOption">
                <cmp-size
                    :size="size" :key="index"
                    @click.native="add(size, index)"
                    style="cursor: pointer"
                    ></cmp-size>
            </div>
        </div>
    </div>
</template>

<script>
import Coffee from './Coffee.vue'
import Size from './Size';
export default {
    props: ['order', 'selectedCategory'],
    data: function() {
        return {
            coffeeList: [
                {id: '0-0', name: 'Original Blend', price: 1.59, priceWeight: 0.5, img: '../../img/coffee_org.png'},
                {id: '0-1', name: 'Dark Rost Coffee', price: 1.59, priceWeight: 0.5, img: '../../img/coffee_dark.png'},
                {id: '0-2', name: 'Decaf', price: 1.59, priceWight: 0.5, img: '../../img/coffee_org.png'},
                {id: '0-3', name: 'Latte', price: 2.79, priceWeight: 0.5, img: '../../img/coffee_latte.png'},
                {id: '0-4', name: 'French Vanilla', price: 1.99, priceWeight: 0.5, img: '../../img/coffee_french.png'},
                {id: '0-5', name: 'Cappuccino', price: 3.40, priceWeight: 1, img: '../../img/coffee_cappuccino.png'}
            ],
            selectedCoffee: null,
            sizeOption: [
                {name: 'Small', initial: 'SM'}, 
                {name: 'Medium', initial: 'M'}, 
                {name: 'Large', initial: 'L'}, 
                {name: 'Extra Large', initial: "XL"}
            ]
        }
    },
    methods: {
        add(theSize, index) {
            if (this.selectedCoffee) {   // only when the kind of the coffee is selected
                console.log('selected');
                let theCoffee = this.selectedCoffee;
                let newCoffeeId = theCoffee.id + '-' + index;
                let newCoffeeName = theCoffee.name + ' ' + theSize.name;
                let theCoffeePrice = theCoffee.price + index * theCoffee.priceWeight;
                let oldIndexOfNewItem = this.order.findIndex(x => x.id == newCoffeeId);
                if (oldIndexOfNewItem == -1) {
                    
                    this.order.push({id: newCoffeeId, name: newCoffeeName, price: theCoffeePrice, amount: 1});
                } else {
                    this.order[oldIndexOfNewItem].amount++;
                }
            } else {
                console.log('not selected');
            }
        },
        back() {
            this.$emit('back');
        }
    },
    components: {
        cmpCoffee: Coffee,
        cmpSize: Size
    }
}
</script>

<style>
</style>
