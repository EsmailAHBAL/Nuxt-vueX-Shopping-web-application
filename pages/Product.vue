<template>
  <section>
    <hr />
    <div v-if="productId">
      <div class="block">
        <div class="card">
          <div class="card-content">
            <div class="block" style="display: flex;justify-content:  space-evenly;">
              <img :src="`${get_TheProduct[0].image}`" />
            </div>
            <div class="block" style="display: flex;justify-content:  space-evenly;">
              <div>
                <h2>Produc ID :</h2>
              </div>
              <div class="tag is-link">
                {{get_TheProduct[0].id}}
              </div>
            </div>
            <div class="block" style="display: flex;justify-content:  space-evenly;">
              <div>
                <h2> product Name:</h2>
              </div>
              <div class="tag is-link">
                {{get_TheProduct[0].productname}}
              </div>
            </div>
            <div class="block" style="display: flex;justify-content:  space-evenly;">
              <div>
                <h2> product Prix:</h2>
              </div>
              <div class="tag is-link">
                {{get_TheProduct[0].prix}}
              </div>
            </div>
            <div class="block" style="display: flex;justify-content:  space-evenly;">
              <div>
                <h2> product Quantity:</h2>
              </div>
              <div class="tag is-link">
                {{get_TheProduct[0].quantity}}
              </div>
            </div>
            <div class="block" style="display: flex;justify-content:  space-evenly;">
              <div style="display: flex;justify-content: space-evenly;">
                <div>
                  <input v-model="lastprice" class="input" placeholder="1" value="1" style="width: 70px;" type="number"
                    pattern=" 0+\.[0-9]*[1-9][0-9]*$"
                    min="0"
                    />
                </div>
                <hr />
                <div style="margin-left: 20px;">

                    <button class="button is-link" @click="getOrder()" > Add To Cart <span style="margin-left: 20px;"
                      class="tag is-dark">{{getPrice}} $ </span></button>

                </div>
                <Adding  style="margin-left: 50px;" v-if="addToCart" @click="addToCart=$event"/>
              </div>

            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="bloc" v-else>
      <h1>Data Not FOUND !!! </h1>
    </div>
  </section>
</template>

<script>
  import {
    mapState
  } from 'vuex';
  import Adding from '~/components/Adding.vue';


  export default {
    data: () => ({
      name: "This For Items 😉",
      productId: 0,
      lastprice: 0,
      addToCart:false
    }),
    computed: {
      ...mapState([
        "shopdata","cart"
      ]),
      get_TheProduct() {
        return this.shopdata.filter(item => {
          if (item.id == this.productId) {
            return item;
          }
        });
      },
      getPrice(){
        return this.lastprice * this.get_TheProduct[0].prix
      }

    },
    watch:{
      lastprice :{
        handler(){
          this.addToCart=false
        }
      }
    },
    mounted() {
      this.productId = this.$route.params.id;
      localStorage.productId = this.productId;
    },
    methods:{
      getOrder() {
        if(this.lastprice ==0 || this.lastprice>this.get_TheProduct[0].quantity){
          this.addToCart=false
          this.lastprice=0
          return
        }

       this.addToCart=true
       let Items ={
        productName :this.get_TheProduct[0].productname,
        price :this.get_TheProduct[0].prix,
        Count :this.lastprice,
        Total :this.getPrice
       }
       this.$store.commit("getOrder",Items)
       let data4u = {
        id:  this.get_TheProduct[0].id,
        q :  this.lastprice
       }
       this.$store.commit("updateDataShop",data4u)
      }
    },
    components: {
      Adding
    }
  }

</script>

<style>
  * {
    user-select: none;
  }

</style>
