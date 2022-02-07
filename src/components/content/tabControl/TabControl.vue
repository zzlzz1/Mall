<template>
  <div class="tab-control">
  <div v-for="(item,index) in titles" 
       :key="index" 
       class="tab-control-item"
       :class="{active: index === currentIndex}"
       @click="currentIndex = index">
    <span>{{item}}</span>
  </div>
 </div>
</template>

<script>
  export default {
    name: 'TabControl',
    data() { 
      return {
        currentIndex: 0
      }
    },
    components:{
      
    },
    props: {
      titles: {
        type: Array,
        default() {
          return []
        }
      }
    }
  }
</script>

<style scoped>
  .tab-control {
    display: flex;
    text-align: center;
    font-size: 15px;
    height: 40px;
    line-height: 40px;
    background-color: #fff;
  }
  .tab-control-item {
    flex: 1;
  }
  .active span{
    padding: 5px;
    color: var(--color-high-text);
    border-bottom: 3px solid var(--color-tint)
  }
</style>