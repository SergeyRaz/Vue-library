<template>
	<div class="gallery">
		<div class="gallery-container">
			<img class="gallery-img"
      v-for="(value, index, key) in arrImg"
      :class="{active : value.status}"
      :key="key"
      :src="value.img" 
      :alt="key">
		</div>
    <carousel 
      :arrImg="arrImg"
      @onView="onView"></carousel>
		<div class="btn-container">
			<input type="button" @click="mLeft()" value="< Назад" class="btn btn-left">
			<input type="button" @click="mRight()" value="Вперед >" class="btn btn-right">
		</div>
	</div>
</template>

<script>
import carousel from './Carousel.vue'
export default {
  components: {
    carousel
  },
  data() {
    return {
      ind: 0,
      isActive: true,
      way: 'src/assets/img/',   // Путь до папки с изображениями
      arrImgWay: ['1.jpg','2.jpg','7.jpg','8.jpg','9.jpg','3.jpg'],
      arrImg: []
    };
  },
  beforeMount(){
    for(let i = 0; i < this.arrImgWay.length; i++){
      if(i == 0){
        this.arrImg.push({img: (this.way + this.arrImgWay[i]), status: true});
      }
      else{
        this.arrImg.push({img: (this.way + this.arrImgWay[i]), status: false});
      }
    }
  },
  methods: {
    mLeft() {
      this.arrImg[this.ind].status = false;
      this.ind--
      if(this.ind >= 0){
        this.arrImg[this.ind].status = true;
      }
      else{
        this.ind = this.arrImg.length-1;
        this.arrImg[this.ind].status = true;
      }
    },
    mRight() {
      this.arrImg[this.ind].status = false;
      this.ind++
      if(this.ind < this.arrImg.length){
        this.arrImg[this.ind].status = true;
      }
      else{
        this.ind = 0;
        this.arrImg[this.ind].status = true;
      }
    },
    onView(index){
      for(let i = 0; i < this.arrImg.length; i++){
        this.arrImg[i].status = false;
      }
      this.ind = index;
      this.arrImg[index].status = true;
    }
  }
};
</script>

<style lang="scss">
* {
  outline: none;
}
img {
  display: block;
  width: 100%;
  height: 100%;
}
.gallery {
  font-family: "Roboto Condensed", sans-serif;
  width: 600px;
  margin: 10px auto;
  position: relative;
  .gallery-container {
    position: relative;
    height: 338px;
    border-bottom: 3px solid #fff;
    border-radius: 3px;
  }
  .gallery-img {
    position: absolute;
    display: none;
    opacity: 0;
  }
  .active {
    display: block;
    opacity: 1;
    animation: anim-opacity 1s ease-out forwards;
  }
  .btn-container {
    position: absolute;
    bottom: -35px;
    left: calc(50% - 76px);
    .btn {
      background-color: darkcyan;
      color: #fff;
      padding: 5px 10px;
      border: 1px solid #fff;
      border-radius: 3px;
      font-family: "Roboto Condensed", sans-serif;
      cursor: pointer;
      &:hover {
        background-color: #008181;
      }
    }
  }
}

@keyframes anim-opacity {
  0%{opacity: 0;}
  100%{opacity: 1;}
}
</style>