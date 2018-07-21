<template>
	<div class="carousel">
		<img class="carousel-img"
      v-for="(value, index, key) in arrImg"
      :class="{active : value.status}"
      :key="key"
      :src="value.img" 
      :alt="key"
			@click="onView(index)">
	</div>
</template>

<script>
export default {
	props: ['arrImg'],
  data() {
    return {
			a: 1
    };
	},
	methods: {
		onView(index){
			this.$emit('onView', index);
		}
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