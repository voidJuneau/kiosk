<template>
    <div class="container-fluid">
        <div class="row" v-if="!selectedTea">
            <button class="btn btn-secondary"
                @click="back">Back to main</button>
        </div>
        <div class="row" v-if="!selectedTea">
            <div class="col-6 col-sm-4 py-3" v-for="tea in teaList">
                <cmp-tea
                    :tea="tea" :key="tea.id" :order="order"
                    @click.native="selectedTea = tea"
                    ></cmp-tea>
            </div>
        </div>
        <div class="row"
            v-if="selectedTea">
            <button class="btn btn-secondary"
                @click="selectedTea = null">Back to Tea</button>
        </div>
        <div class="row"
            v-if="selectedTea">
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
import Tea from './Tea.vue'
import Size from './Size';
export default {
    props: ['order', 'selectedCategory'],
    data: function() {
        return {
            teaList: [
                {id: '1-0', name: 'Loose Leaf', price: 1.59, priceWeight: 0.2, img:'../../img/tea_loose.png'},
                {id: '1-1', name: 'Green Tea', price: 1.59, priceWeight: 0.2, img:'../../img/tea_green.png'},
                {id: '1-2', name: 'Honey Lemon Herbal', price: 1.59, priceWeight: 0.2, img:'../../img/tea_honey.png'},
                {id: '1-3', name: 'Orange Pekoe', price: 1.59, priceWeight: 0.2, img:'../../img/tea_orange.png'},
                {id: '1-4', name: 'Earl Grey', price: 1.59, priceWeight: 0.2, img:'../../img/tea_grey.png'},
                {id: '1-5', name: 'Peppermint Herbal', price: 1.59, priceWeight: 0.2, img:'../../img/tea_peppermint.png'},
                {id: '1-6', name: 'Chai', price: 1.59, priceWeight: 0.2, img:'../../img/tea_chai.png'},
                {id: '1-7', name: 'Chamomile Herbal', price: 1.59, priceWeight: 0.2, img:'../../img/tea_chamomile.png'},
                {id: '1-8', name: 'English Breakfast', price: 1.59, priceWeight: 0.2, img:'../../img/tea_english.png'},
                {id: '1-9', name: 'Apple Cinnamon Herbal', price: 1.59, priceWeight: 0.2, img:'../../img/tea_apple.png'}
            ],
            selectedTea: null,
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
            if (this.selectedTea) {   // only when the kind of the tea is selected
                console.log('selected');
                let theTea = this.selectedTea;
                let newTeaId = theTea.id + '-' + index;
                let newTeaName = theTea.name + ' ' + theSize.name;
                let theTeaPrice = theTea.price + index * theTea.priceWeight;
                let oldIndexOfNewItem = this.order.findIndex(x => x.id == newTeaId);
                if (oldIndexOfNewItem == -1) {
                    
                    this.order.push({id: newTeaId, name: newTeaName, price: theTeaPrice, amount: 1});
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
        cmpTea: Tea,
        cmpSize: Size
    }
}
</script>

<style>
</style>
