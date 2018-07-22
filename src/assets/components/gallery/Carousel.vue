<template>
	<div class="carousel">
		<div class="carousel-block"
		:style="shift">
			<img class="carousel-img"
      v-for="(value, index, key) in arrImg"
      :class="{active : value.status}"
      :key="key"
      :src="value.img" 
      :alt="key"
			@click="onView(index)">
		</div>
	</div>
</template>

<script>
export default {
  props: ["arrImg"],
  data() {
    return {
      shift: ''
    };
  },
  methods: {
    onView(index) {
      if(index < (this.arrImg.length - 2)){
        this.shift = 'left: -' + (153*(index-1)) + 'px;'
      }
      this.$emit("onView", index);
    }
  }
};
</script>

<style lang="scss">
.carousel {
	height: 85px;
	position: relative;
	overflow: hidden;
  .carousel-block {
		position: absolute;
    display: flex;
		height: 85px;
		transition: 1s;
    left: 0;
    .carousel-img {
      box-sizing: border-box;
      width: 151px;
      height: 85px;
      border-right: 3px solid #fff;
      cursor: pointer;
      &:last-child {
        border: none;
      }
    }
  }
}
</style>