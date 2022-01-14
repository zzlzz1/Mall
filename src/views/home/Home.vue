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
	export default {
		name: "Home",
		data() {
			return {
				
			}
		},
		components: {
			NavBar
		}
	}
</script>
 
<style scoped>
	.home-nav {
		background-color: var(--color-tint);
		color: white;
	}
</style>