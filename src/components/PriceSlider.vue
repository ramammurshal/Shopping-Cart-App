<template>
  <div class="align-items-center my-3 animate__animated animate__bounceInDown" :class="sliderState">
    <label>Maximum Price</label>
    <input type="number" class="form-control mx-2" style="width: 60px" v-model="maxAmount" @change="$emit('update:maximum', maxAmount)" />
    <input type="range" class="form-range" min="0" max="100" v-model="maxAmount" @input="$emit('update:maximum', maxAmount)" />
  </div>
</template>

<script>
export default {
  name: "price-slider",
  data: function () {
    return {
      maxAmount: 20,
    };
  },
  props: ["sliderStatus", "maximum"],
  computed: {
    sliderState: function () {
      return this.sliderStatus ? "d-flex" : "d-none";
    },
  },
};
</script>
