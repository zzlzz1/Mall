<template>
	<div id="home">
		<nav-bar class="home-nav">
			<template v-slot:center>
				<div>购物街</div>
			</template>
		</nav-bar>
	</div>
</template>
 
<script>
	import NavBar from "components/common/navbar/NavBar";
	import {getMultiData} from "network/home";
	export default {
		name: "Home",
		data() {
			return {
				banners: [],
				dkeywords: [],
				keyworkds: [],
				recommends: []
			}
		},
		components: {
			NavBar
		},
		created() {
			getMultiData().then((res) => {
				console.log(res);
				this.banners = res.data.banner.list;
				console.log(this.banners);
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