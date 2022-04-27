<template>
  <div class="goods">
    <goods-list-item class="item" v-for="(item, index) in goods" :key="index" :goods-item="item"/>
 </div>
</template>

<script>
  import GoodsListItem from "./GoodsListItem"
  export default {
    name: 'GoodsList',
    data() { 
      return {
      }
    },
    props: {
      goods: {
        type: Array,
        default() {
          return [];
        }
      }
    },
    components:{
      GoodsListItem
      
    }
  }
</script>

<style scoped>
    .goods {
    display: flex;
    flex-wrap: wrap;
    padding: 5px;
    justify-content: space-around;
  }

  .goods .item {
    width: 48%;
  }
</style>