<template>
    <div class="mt-5">
        <div class="row">
            <cmp-order-item class="my-2" v-for="(item, index) in order" :item="item" :key="index" :index="index" :order="order"></cmp-order-item>
            <!-- <p>{{order[0].name}}</p> -->
        </div>
        <div class="row">
            <p class="m-0 mt-4">total price: {{ totalPrice.toFixed(2) }}</p>
        </div>
        <div class="row">
            <div class="col"></div>
            <a href="#placeorder">
                <button class="btn btn-secondary btn-sm"
                    data-toggle="modal" data-target="#placeorderModal">Place order</button>
            </a>
        </div>

        <div class="modal fade" id="placeorderModal" role="dialog">
            <div class="modal-dialog modal-lg modal-notify modal-info modal-success" role="content">
                <div class="modal-content">
                    <div class="modal-header">
                        <h4 class="modal-title">Order detail</h4>
                        <button class="close" type="button" data-dismiss="modal"
                            >&times;</button>
                    </div>
                    <div class="class modal-body mx-2">
                        <div class="row">
                            <cmp-order-detail-item v-for="(item, index) in order" :item="item" :key="index" :index="index" :order="order"></cmp-order-detail-item>
                        </div>
                        <div class="row mt-2">
                            <p>total price: {{ totalPrice.toFixed(2) }}</p>
                        </div>
                        <div class="row">
                            <div class="col"></div>
                            <button type="button" data-dismiss="modal" class="btn btn-secondary btn-sm" id="confirm">Cancel</button>
                            <button type="button" data-dismiss="modal" class="btn btn-secondary btn-sm"
                                @click.prevent="orderConfirm">Confirm</button>
                        </div>
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import OrderItem from './OrderItem'
import OrderDetailItem from './OrderDetailItem'
export default {

    props: ['order'],
    data: function() {
        return {

        }
    },
    methods: {
        orderConfirm() {
            this.order.splice(0, this.order.length);
            this.back();
            alert("Thanks for order!");
        },
        back() {
            this.$emit('back');
        }
    },
    computed: {
        totalPrice() {
            let total = 0;
            for (let i = 0; i < this.order.length; i++) {
                total += this.order[i].price * this.order[i].amount;
            }
            return total;
        }
    },
    components: {
        cmpOrderItem: OrderItem,
        cmpOrderDetailItem: OrderDetailItem
    }
};
</script>

<style>
</style>
