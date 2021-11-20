<template>
  <div>
    <navbar :cart="cart" :cartQty="cartQty" :cartTotal="cartTotal" @toggle-slide="toggleSlider" @delete-item="deleteItem"></navbar>
    <div class="container p-3">
      <h1 class="mt-2">Salsa Shop</h1>
      <price-slider :sliderStatus="sliderStatus" :maximum.sync="maximum"></price-slider>
      <product-list :maximum="maximum" :products="products" @add-item="addItem"></product-list>
    </div>
  </div>
</template>

<script>
import Navbar from "./Navbar.vue";
import PriceSlider from "./PriceSlider.vue";
import ProductList from "./ProductList.vue";

export default {
  name: "products",
  props: [
    "products",
    "maximum",
    "cart",
    "cartQty",
    "cartTotal",
    "sliderStatus",
    "sliderState"
  ],
  components: {
    Navbar, PriceSlider, ProductList
  },
  methods: {
    toggleSlider: function() {
      this.$emit('toggle');
    },
    addItem: function(item) {
      this.$emit('add', item)
    },
    deleteItem: function(index) {
      this.$emit('delete', index);
    },
  },
}
</script>
