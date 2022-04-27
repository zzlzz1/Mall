<template>
	<div id="home">
		<nav-bar class="home-nav">
			<template v-slot:center>
				<div>购物街</div>
			</template>
		</nav-bar>
		<home-swiper :banners="banners"/>
		<recommend-view :recommends= "recommends"/>
		<feature-view/>
		<tab-control class="tab-control" 
		:titles="['流行','新款','精选']" 
		@tabClick="tabClick"/>
		<goods-list :goods="goods[currentType].list"/>
	</div> 
</template>
 
<script>
	import HomeSwiper from "./childComps/HomeSwiper";
	import RecommendView from "./childComps/RecommendView";
	import FeatureView from "./childComps/FeatureView"

	import NavBar from "components/common/navbar/NavBar";
	import TabControl from "components/content/tabControl/TabControl";
	import GoodsList from "components/content/goods/GoodsList";

	
  import {getMultiData, getHomeGoods} from "network/home";
	export default {
		name: "Home",
		data() {
			return {
				banners: [],
				recommends: [],
				goods: {
					pop: {page: 0, list: []},
					new: {page: 0, list: []},
					sell: {page: 0, list: []},
				},
				currentType: "pop"
			}
		},
		components: {
			HomeSwiper,
			RecommendView,
			FeatureView,
			NavBar,
			TabControl,
			GoodsList
		},
		created() {
			this.getMultiData();
			this.getHomeGoods("pop");
			this.getHomeGoods("new");
			this.getHomeGoods("sell");

			
		},
		methods: {
			/**
			 * 网络请求相关
			 */
			getMultiData(){
				getMultiData().then((res) => {
				this.banners = res.data.banner.list;
				this.recommends = res.data.recommend.list;
			});
			},
			getHomeGoods(type){
				const page = this.goods[type].page + 1;
				getHomeGoods(type, page).then(res => {
					//console.log(res);
					this.goods[type].list.push(...res.data.list);
					this.goods[type].page = page;
					// this.goods[type].page++;
					// this.goods[type].page += 1;
					
					//console.log(this.goods[type].page);
				});
			},
			/**
			 * 时间监听相关
			 */
			tabClick(index){
				switch(index) {
					case 0:
						this.currentType = "pop";
						break;
					case 1:
						this.currentType = "new";
						break;
					case 2:
						this.currentType = "sell";
						break;
				}
			}
		}
	}
</script>
 
<style scoped>
	#home {
		padding-top: 44px;
	}
	.home-nav {
		background-color: var(--color-tint);
		color: white;
		position: fixed;
		left: 0;
		right: 0;
		top: 0;
		z-index: 9;
	}
	.tab-control {
		position: sticky;
		top: 43px;
		z-index: 9;
	}
</style>