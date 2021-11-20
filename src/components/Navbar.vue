<template>
  <nav class="navbar navbar-dark bg-dark sticky-top">
    <div class="container d-flex align-items-center justify-content-md-center">
      <div class="dropdown m-2" v-if="cart.length > 0">
        <button class="btn btn-success dropdown-toggle" type="button" id="dropDownListBelanjaan" data-bs-toggle="dropdown" aria-expanded="false">
          <span class="badge bg-warning rounded-pill me-2">{{ cartQty }}</span>
          <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
          <price :value="Number(cartTotal)"></price>
        </button>
        <ul class="dropdown-menu" aria-labelledby="dropDownListBelanjaan" style="width: 280px">
          <li v-for="(item, index) in cart" :key="index" class="p-2">
            <div class="d-flex align-items-center justify-content-between">
              <span class="badge bg-warning text-dark mx-1">{{ item.qty }}</span>
              <span style="font-size: 12px">{{ item.product.name }}</span>
              <b class="mx-1">{{ (item.product.price * item.qty) | currencyFormat }}</b>
              <a href="#" class="badge bg-danger text-white text-decoration-none" @click.stop="$emit('delete-item', index)">-</a>
            </div>
          </li>
          <router-link class="btn btn-sm btn-outline-info text-dark float-end me-2" to="/checkout">Checkout</router-link>
        </ul>
      </div>
      <button class="btn btn-outline-success m-2" @click="$emit('toggle-slide')">
        <font-awesome-icon icon="dollar-sign"></font-awesome-icon>
        Filter Harga
      </button>
    </div>
  </nav>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import Price from "./Price.vue";

export default {
  name: "navbar",
  components: {
    FontAwesomeIcon,
    Price,
  },
  props: ["cart", "cartQty", "cartTotal"],
  filters: {
    currencyFormat: function (value) {
      return "Rp" + Number.parseFloat(value).toFixed(2);
    },
  },
};
</script>
