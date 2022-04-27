<template>
	<div>
		<tab-bar class="tab-bar">
      <tab-bar-item path="/home">
        <!-- vue3插槽的写法 -->
        <template v-slot:item-icon>
          <img src="~assets/img/tabbar/home.svg" alt="">
        </template>
        <template v-slot:item-icon-active>
          <img src="~assets/img/tabbar/home_active.svg" alt="">
        </template>
        <template v-slot:item-text>
          <div>首页</div>v
        </template>
      </tab-bar-item>
      <tab-bar-item path="/category">
        <!-- vue2插槽的写法 -->
        <img slot="item-icon" src="~assets/img/tabbar/category.svg" alt="">
        <img slot="item-icon-active" src="~assets/img/tabbar/category_active.svg" alt="">
        <div slot="item-text">分类</div>
      </tab-bar-item>
      <tab-bar-item path="/shopcart">
        <img slot="item-icon" src="~assets/img/tabbar/shopcart.svg" alt="">
        <img slot="item-icon-active" src="~assets/img/tabbar/shopcart_active.svg" alt="">
        <div slot="item-text">购物车</div>
      </tab-bar-item>
      <tab-bar-item path="/profile">
        <img slot="item-icon" src="~assets/img/tabbar/profile.svg" alt="">
        <img slot="item-icon-active" src="~assets/img/tabbar/profile_active.svg" alt="">
        <div slot="item-text">我的</div>
      </tab-bar-item>
    </tab-bar>
	</div>
</template>
 
<script>
  import TabBar from 'components/common/tabbar/TabBar';
  import TabBarItem from "components/common/tabbar/TabBarItem";

	export default {
		name: 'MainTabBar',
		data() {
			return {
			}
		},
		components: {
      TabBar,
      TabBarItem
    }
	}
</script>
 
<style scoped>
  .tab-bar {
    z-index: 9;
  }
	
</style>