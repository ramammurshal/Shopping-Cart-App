<template>
  <div class="container p-5">
    <h1>Checkout</h1>
    <!-- Jika cart berisi, maka tampilkan table -->
    <table class="table table-hover table-responsive" v-if="cart.length">
      <caption class="text-end h3">
        <b>Total:</b>
        <price class="d-block text-success fw-bold" :value="Number(cartTotal)"></price>
      </caption>
      <thead>
        <tr>
          <th scope="col"></th>
          <th scope="col">Item</th>
          <th scope="col" class="text-center">Qty</th>
          <th scope="col" class="text-end">Price</th>
          <th scope="col" class="text-end">Sub-Total</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in cart" :key="item.product.id">
          <td class="text-center">
            <div class="btn-group">
              <button @click="$emit('add', item.product)" class="btn btn-info">+</button>
              <button @click="$emit('delete', index)" class="btn btn-outline-info">-</button>
            </div>
          </td>
          <th scope="row">{{ item.product.name }}</th>
          <th class="text-center">{{ item.qty }}</th>
          <th class="text-end">{{ Number(item.product.price) }}</th>
          <th class="text-end">
            {{ Number(item.product.price * item.qty) }}
          </th>
        </tr>
      </tbody>
    </table>
    <router-link class="btn btn-sm btn-outline-info text-dark" to="/">Back to Shop</router-link>
  </div>
</template>

<script>
import Price from "./Price.vue";

export default {
  name: "checkout",
  props: ["cart", "cartTotal"],
  components: {
    Price
  },
}
</script>
