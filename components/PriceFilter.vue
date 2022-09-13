<template>
  <div class="block">
   <div class="block" style="display: flex;justify-content: space-evenly;">
    <h2>Select The Best Price For You  😉 </h2> <p class="tag is-danger">{{select}}</p>
   </div>
     <div class="select block" style="display: flex;justify-content: center;">
      <select :id="select" @change="$emit('change', $event.target.value)" >
      <option :value="select"> More Than  {{select}} $</option>
      <option v-for="option in optionForSelect" :key="option" :value="option"> + {{option}}</option>
      </select>
     </div>
  </div>
</template>

<script>
  export default {
    props :{
      select :{
        type: Number,
        default :0
      },
      optionForSelect :{
        type:Array,
        default :()=>[10,50,80,90,100],
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>
