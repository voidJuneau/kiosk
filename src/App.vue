<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12 col-sm-9">
        <div class="row row-eq-height">
          <div class="col-6 col-sm-4 py-3"
            v-if="!selectedCategory" v-for="(category, index) in categories">
            <cmp-category-menu
              :key="index" :category="category"
              @click.native="[selectedCategoryName=category.name, selectedCategory=category]"
              ></cmp-category-menu>
          </div>
          
          <cmp-coffee-menu
            v-if="selectedCategory == categories[0]" :order="order"
            @back="selectedCategory=null"
          ></cmp-coffee-menu>

          <cmp-tea-menu
            v-if="selectedCategory == categories[1]" :order="order"
            @back="selectedCategory=null"
          ></cmp-tea-menu>

          <cmp-cold-menu
            v-if="selectedCategory == categories[2]" :order="order"
            @back="selectedCategory=null"
          ></cmp-cold-menu>

          <cmp-donut-menu
            v-if="selectedCategory == categories[3]" :order="order"
            @back="selectedCategory=null"
          ></cmp-donut-menu>

          <cmp-breakfast-menu
            v-if="selectedCategory == categories[4]" :order="order"
            @back="selectedCategory=null"
          ></cmp-breakfast-menu>

          <cmp-sandwich-menu
            v-if="selectedCategory == categories[5]" :order="order"
            @back="selectedCategory=null"
          ></cmp-sandwich-menu>

        </div>
      </div>
    

      <cmp-order-list v-if="order.length > 0" :order="order"
        @back="selectedCategory=null"
        class="col-12 col-sm-3"></cmp-order-list>
    </div>
  </div>
</template>

<script>
import CategoryMenu from './cmp/CategoryMenu.vue';
import CoffeeMenu from './cmp/CoffeeMenu.vue';
import TeaMenu from './cmp/TeaMenu.vue';
import ColdMenu from './cmp/ColdMenu.vue';
import DonutMenu from './cmp/DonutMenu.vue';
import BreakfastMenu from './cmp/BreakfastMenu.vue';
import SandwichMenu from './cmp/SandwichMenu.vue';
import OrderList from './cmp/OderList.vue';
export default {
  data: function() {
    return {
      categories: [{ name: 'Coffee', img: '../img/coffee_org.png'}, 
                   { name: 'Tea' , img: '../img/tea_specialty.png'}, 
                   { name: 'Cold', img: '../img/cold_real.png'}, 
                   { name: 'Donut', img: '../img/donut.png'},
                   { name: 'Breakfast', img: '../img/breakfast_oatmeal.png'},
                   { name: 'Sandwich', img: '../img/sandwich_turkey.png'}
                   ],
      selectedCategory: null,
      order: []
    };
  },
  components: {
    cmpCategoryMenu: CategoryMenu,
    cmpCoffeeMenu: CoffeeMenu,
    cmpTeaMenu: TeaMenu,
    cmpColdMenu: ColdMenu,
    cmpDonutMenu: DonutMenu,
    cmpBreakfastMenu: BreakfastMenu,
    cmpSandwichMenu: SandwichMenu,
    cmpOrderList: OrderList
  }
};

</script>

<style>

/* .container-fluid {
    padding: 0px;
    margin: 0px;
} */
</style>
