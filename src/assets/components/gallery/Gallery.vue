<template>
	<div class="gallery">
		<div class="gallery-container">
			<img class="gallery-img"
      v-for="(value, index, key) in arrImg"
      :class="{active : value.status}"
      :key="key"
      :src="value.img" 
      :alt="key">
      <div @click="prevHendler" class="btn btn-left"><i class="fas fa-hand-point-left"></i></div>
			<div @click="nextHendler" class="btn btn-right"><i class="fas fa-hand-point-right"></i></div>
		</div>

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
	</div>
</template>

<script>
export default {
  data() {
    return {
      shift: "",
      shiftNumber: 120,
      ind: 0,
      isActive: true,
      way: "src/assets/img/", // Путь до папки с изображениями
      arrImgWay: ["1.jpg", "2.jpg", "3.jpg", "4.jpg", "5.jpg", "6.jpg", "7.jpg", "8.jpg", "9.jpg", "10.jpg",],
      arrImg: []
    };
  },
  beforeMount() {
    for (let i = 0; i < this.arrImgWay.length; i++) {
      if (i == 0) {
        this.arrImg.push({ img: this.way + this.arrImgWay[i], status: true });
      } else {
        this.arrImg.push({ img: this.way + this.arrImgWay[i], status: false });
      }
    }
  },
  methods: {
    prevHendler() {
      this.arrImg[this.ind].status = false;
      this.ind--;
      if (this.ind >= 0) {
        this.arrImg[this.ind].status = true;
      } else {
        this.ind = this.arrImg.length - 1;
        this.arrImg[this.ind].status = true;
      }

      if (this.ind < this.arrImg.length - 3) {
        this.shift = `left: -${this.shiftNumber * this.ind + -240}px;`;
      } else {
        this.shift = `left: -${this.shiftNumber * (this.arrImg.length-5)}px;`;
      }
      console.log(this.arrImg.length);
      console.log(this.ind);
    },
    nextHendler() {
      this.arrImg[this.ind].status = false;
      this.ind++;
      if (this.ind < this.arrImg.length) {
        this.arrImg[this.ind].status = true;
      } else {
        this.ind = 0;
        this.arrImg[this.ind].status = true;
      }

      if (this.ind > 2 && this.ind < this.arrImg.length - 2) {
        this.shift = `left: -${this.shiftNumber * this.ind + -240}px;`;
      } else if (this.ind == 0) {
        this.shift = `left: -${this.shiftNumber * this.ind}px;`;
      }
    },
    onView(index) {
      this.ind = index;
      for (let i = 0; i < this.arrImg.length; i++) {
        this.arrImg[i].status = false;
      }

      this.arrImg[this.ind].status = true;
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
  -webkit-user-select: none;
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
    &:hover .btn {
      display: block;
      opacity: 1;
      animation: anim-opacity 0.3s ease-out forwards;
    }
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
  .btn {
    opacity: 0;
    position: absolute;
    top: calc(50% - 30px);
    color: #fff;
    cursor: pointer;
    svg {
      width: 60px;
      height: 60px;
      stroke: #444;
      stroke-width: 10px;
      transition: 0.3s;
      &:hover {
        transform: scale(1.2);
      }
    }
  }
  .btn-left {
    left: 10px;
  }
  .btn-right {
    right: 10px;
  }
}
.carousel {
  height: 70px;
  position: relative;
  overflow: hidden;
  .carousel-block {
    position: absolute;
    display: flex;
    height: 70px;
    transition: 1s;
    left: 0;
    .active {
      border: 3px solid darkorange;
    }
    .carousel-img {
      box-sizing: border-box;
      width: 120px;
      height: 70px;
      // border-right: 3px solid #fff;
      cursor: pointer;
      // &:last-child {
      //   border: none;
      // }
    }
  }
}
@keyframes anim-opacity {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>