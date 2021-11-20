<template>
  <div>
    <div class="row mb-3 p-3 align-items-center rounded-3 animate__animated animate__fadeInLeft" v-for="(item, index) in showItem" :key="index" style="background-color: #e3e3e3">
      <!-- Col-1 -->
      <div class="col-1">
        <button class="btn btn-warning" @click="$emit('add-item', item)">Beli</button>
      </div>

      <!-- Col-2 -->
      <div class="col-sm-4">
        <img :src="item.image" :alt="item.name" class="img-fluid d-block" />
      </div>

      <!-- Col-3 -->
      <div class="col">
        <h3 class="text-info">{{ item.name }}</h3>
        <p class="mb-0">{{ item.description }}</p>
        <div class="h5 float-end">
          <price :value="Number(item.price)"></price>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Price from "./Price.vue";

export default {
  name: "product-list",
  components: {
    Price,
  },
  props: ["products", "maximum"],
  // maximum disini me-refer kepada maximum price
  computed: {
    showItem: function () {
      let max = this.maximum;
      return this.products.filter(function (item) {
        return Number(item.price) <= max;
      });
    },
  },
};
</script>
