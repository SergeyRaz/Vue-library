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
		<div class="btn-container">
			<input type="button" @click="mLeft()" value="< Назад" class="btn btn-left">
			<input type="button" @click="mRight()" value="Вперед >" class="btn btn-right">
		</div>
	</div>
</template>

<script>
export default {
  data() {
    return {
      in: 0,
      isActive: true,
      arrImgWay: ['src/assets/img/1.jpg','src/assets/img/2.jpg','src/assets/img/7.jpg','src/assets/img/8.jpg','src/assets/img/9.jpg','src/assets/img/3.jpg'],
      arrImg: []
    };
  },
  beforeMount(){
    for(let i = 0; i < this.arrImgWay.length; i++){
      if(i == 0){
        this.arrImg.push({img: this.arrImgWay[i], status: true});
      }
      else{
        this.arrImg.push({img: this.arrImgWay[i], status: false});
      }
    }
  },
  computed: {

  },
  methods: {
    mLeft() {
      this.arrImg[this.in].status = false;
      this.in--
      if(this.in >= 0){
        this.arrImg[this.in].status = true;
      }
      else{
        this.in = this.arrImg.length-1;
        this.arrImg[this.in].status = true;
      }
    },
    mRight() {
      this.arrImg[this.in].status = false;
      this.in++
      if(this.in < this.arrImg.length){
        this.arrImg[this.in].status = true;
      }
      else{
        this.in = 0;
        this.arrImg[this.in].status = true;
      }
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
  border: 3px solid darkcyan;
  border-radius: 3px;
  .gallery-container {
    height: 338px;
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