<template>
    <div class="container-fluid">
        <div class="row" v-if="!selectedCold">
            <button class="btn btn-secondary"
                @click="back">Back to main</button>
        </div>
        <div class="row" v-if="!selectedCold">
            <div  class="col-6 col-sm-4 py-3" v-for="cold in coldList" >
                <cmp-cold
                    :cold="cold" :key="cold.id" :order="order"
                    @click.native="selectedCold = cold"></cmp-cold>
            </div>

        </div>
        <div class="row"
            v-if="selectedCold">
            <button class="btn btn-secondary"
                @click="selectedCold = null">Back to Cold</button>
        </div>
        <div class="row"
            v-if="selectedCold">
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
import Cold from './Cold.vue'
import Size from './Size';
export default {
    props: ['order', 'selectedCategory'],
    data: function() {
        return {
            coldList: [
                {id: '2-0', name: 'Real Fruit Chill', price: 1.49, priceWeight: 0.3, img: '../../img/cold_real.png'},
                {id: '2-1', name: 'Frozen Lemonade', price: 1.49, priceWeight: 0.3, img: '../../img/cold_lemonade.png'},
                {id: '2-2', name: 'Fruit Smoothie Made with Greek Yogurt', price: 2.79, priceWeight: 0.6, img: '../../img/cold_fruit.png'},
                {id: '2-3', name: 'Creamy Chocolate Chill', price: 2.49, priceWeight: 0.5, img: '../../img/cold_chocolate.png'}
            ],
            selectedCold: null,
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
            if (this.selectedCold) {   // only when the kind of the cold is selected
                console.log('selected');
                let theCold = this.selectedCold;
                let newColdId = theCold.id + '-' + index;
                let newColdName = theCold.name + ' ' + theSize.name;
                let theColdPrice = theCold.price + index * theCold.priceWeight;
                console.log(theColdPrice);
                let oldIndexOfNewItem = this.order.findIndex(x => x.id == newColdId);
                if (oldIndexOfNewItem == -1) {
                    
                    this.order.push({id: newColdId, name: newColdName, price: theColdPrice, amount: 1});
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
        cmpCold: Cold,
        cmpSize: Size
    }
}
</script>

<style>
</style>
