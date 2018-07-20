<template>
	<div class="carousel">
		<img class="carousel-img" src="src/assets/img/1.jpg">
		<img class="carousel-img" src="src/assets/img/2.jpg">
		<img class="carousel-img" src="src/assets/img/3.jpg">
		<img class="carousel-img" src="src/assets/img/4.jpg">
	</div>
</template>

<script>
export default {
  data() {
    return {

    };
	},
	methods: {

	}
};
</script>

<style lang="scss">
.carousel{
	display: flex;
	.carousel-img{
		box-sizing: border-box;
		width: 25%;
		height: 85px;
    border-right: 3px solid #fff;
		cursor: pointer;
		&:last-child{
			border: none;
		}
	}
}
</style>