<template>
  <div>
<Cover />
<hr />
<price-filter @change="selectPrice= $event"></price-filter>
  <Menu  :dataSOurce="dataFilter" />
  </div>
</template>

<script>
import Cover from '@/components/Cover.vue';
import Menu from './Menu.vue';
import PriceFilter from './PriceFilter.vue';
import { mapState } from 'vuex';

  export default {
    components: { Cover, Menu, PriceFilter }
    ,
    data:()=>({
      selectPrice : ""
    }),
      computed: {
        ...mapState([
          'shopdata',
        ]),
        dataFilter(){
         return this,this.shopdata.filter(item =>{
          if(item.prix >this.selectPrice){
            return item
          }
         })
        }
      },
    };
</script>

<style lang="scss" scoped>

</style>
