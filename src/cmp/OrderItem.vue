<template>
    <div class="d-flex flex-wrap">
        <!-- <span>
          {{ item.id }}
        </span> -->
        <div class="p-0">
          {{ item.name }} {{ item.price.toFixed(2) }}
        </div>
        <div class="p-0">
          <input type="number" v-model="item.amount" min="1">
        </div>
        <div class="d-none d-sm-block col"></div>
        <div class="ml-auto p-0">
          {{ (item.price * item.amount).toFixed(2) }}
        </div>
        <div class="ml-auto p-0">
            <button class="btn btn-secondary btn-sm " 
            @click="deleteItem">Delete</button>
        </div>
          
    </div>
</template>

<script>
export default {
  props: ["order", "item", "index"],
  data: function() {
    return {};
  },
  methods: {
    deleteItem() {
      this.order.splice(this.index, 1);
    }
  }
};
</script>

<style>
input[type="number"] {
  width: 40px;
}
</style>
