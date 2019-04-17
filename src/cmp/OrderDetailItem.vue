<template>
  <div class="container">
      <div class="row">
        {{ item.name }} &nbsp; {{ item.price.toFixed(2) }} &nbsp; {{ item.amount }}
        <div class="col"></div>
        {{ (item.price * item.amount).toFixed(2) }}
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
