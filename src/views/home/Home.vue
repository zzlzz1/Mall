<template>
	<div id="home">
		<nav-bar class="home-nav">
			<template v-slot:center>
				<div>购物街</div>
			</template>
		</nav-bar>
		<home-swiper :banners="banners"/>
		<recommend-view :recommends= "recommends"/>
	</div> 
</template>
 
<script>
	import {getMultiData} from "network/home";
	import NavBar from "components/common/navbar/NavBar";
	import HomeSwiper from "./childComps/HomeSwiper";
	import RecommendView from "./childComps/RecommendView";
	
	export default {
		name: "Home",
		data() {
			return {
				banners: [],
				recommends: []
			}
		},
		components: {
			NavBar,
			HomeSwiper,
			RecommendView
		},
		created() {
			getMultiData().then((res) => {
				this.banners = res.data.banner.list;
				this.recommends = res.data.recommend.list;
			});
		}
	}
</script>
 
<style scoped>
	.home-nav {
		background-color: var(--color-tint);
		color: white;
	}
</style>