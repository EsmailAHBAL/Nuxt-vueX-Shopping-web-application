<template>
   <div class="container">
   <div class="columns is-multiline">
    <div class="column is-6" v-for="item in cart" :key="item.id">
      <div class="card">
      <div class="card-content">
        <div class="block" style="display: flex;justify-content:space-evenly ;">
          <div>Product Name </div>
          <div>{{item.productName}}</div>
        </div>
        <div class="block" style="display: flex;justify-content:space-evenly ;">
          <div>Price </div>
          <div>{{item.price}}</div>
        </div>
        <div class="block" style="display: flex;justify-content:space-evenly ;">
          <div>count </div>
          <div>{{item.Count}}</div>
        </div>
        <hr />
          <div class="block" style="display: flex;justify-content:space-evenly ;">
            <h2>Total</h2>
            <span class="tag is-dark">
              {{item.Total}}
            </span>
          </div>
      </div>
      </div>
    </div>
   </div>

  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  computed: {
    ...mapState([
      'cart',
    ])
  },
};
</script>

<style lang="scss" scoped>

</style>
