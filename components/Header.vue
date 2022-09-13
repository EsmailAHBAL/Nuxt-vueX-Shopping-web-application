<template>
<div style="display: flex;justify-content: space-evenly;">
  <a-menu  mode="horizontal">
    <a-menu-item key="mail">

   <nuxt-link to="/">Home 🏠</nuxt-link>
    </a-menu-item>

    <a-sub-menu key="sub1">
      <template #title>More  <span>➕ </span></template>
      <a-menu-item-group title="Know More Details">
        <a-menu-item key="setting:1">About Us </a-menu-item>
        <a-menu-item key="setting:2">Contac US </a-menu-item>
      </a-menu-item-group>


    </a-sub-menu>

  </a-menu>
<a-menu>

    <a-menu-item key="mail2" style="position: relative;">

<nuxt-link to="/cart" >Cart 🛒 <span class="tag is-danger is-rounded"  v-if="count>0">{{count}}</span></nuxt-link>
 </a-menu-item>
</a-menu>

  </div>
</template>
<script>
  import { mapState } from 'vuex';
import { defineComponent, ref } from 'vue';
import { MailOutlined, AppstoreOutlined, SettingOutlined } from '@ant-design/icons-vue';
export default{
  computed: {
      ...mapState([
        'count',
      ])
  }
}
</script>
