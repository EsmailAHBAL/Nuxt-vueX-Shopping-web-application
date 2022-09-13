<template>
  <div>
    <div class="ifNot block" v-if="dataSOurce.length == 0">
      <div class="notification is-warning">
        Sorry 😮
        <div>
          <h2>Select Anthor Price </h2>
        </div>
      </div>
    </div>
    <div class="columns is-multiline" v-else>
      <div class="column is-4" v-for="data in dataSOurce" :key="data.id">
        <div class="card">
          <div class="card-content">
            <div class="block">
              <h2 class="tag is-dark">{{data.productname}}</h2>
            </div>
            <div class="block">
              <img :src="data.image" />
            </div>
            <div class="block">
              <div style="display: flex;justify-content: start;">
                <span class="tag is-dark">Prix </span>
                <div style="margin-left: 20px;" class="tags are-large">
                  <span class="tag is-danger" style="position: relative;top: -10px;"> 💰 {{data.prix}} </span>
                </div>
              </div>
            </div>
            <div class="block">
              <div style="display: flex;justify-content: start;">
                <span class="tag is-dark">quantity </span>
                <div style="margin-left: 20px;" class="tags are-large">
                  <span class="tag is-danger" style="position: relative;top: -10px;"> 🏪 {{data.quantity}} </span>
                </div>
              </div>
            </div>

            <div class="block" style="display: flex;justify-content: center;">
              <nuxt-link :to='`/product/${data.id}`'>
                  <button class="button is-warning" >Buy 🧺 </button>
                </nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>


  export default {
    props :{
      dataSOurce:{
        typeof :[Array,Object]
      }
    },
  };

</script>

<style lang="scss" scoped>

</style>
