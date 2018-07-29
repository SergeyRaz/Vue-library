<template>
	<div class='gallery'>
		<div class='gallery-container'>
			<img class='gallery-img'
      v-for='(value, index, key) in arrayPathsImages'
      :class='{active : value.status}'
      :key='key'
      :src='value.img' 
      :alt='key'>
      <div @click='prevHendler' class='btn btn-left'><i class='fas fa-hand-point-left'></i></div>
			<div @click='nextHendler' class='btn btn-right'><i class='fas fa-hand-point-right'></i></div>
		</div>

    <div class='carousel'>
      <div class='carousel-block'
      :style='offsetLeft'>
        <img class='carousel-img'
        v-for='(value, index, key) in arrayPathsImages'
        :class='{active : value.status}'
        :key='key'
        :src='value.img' 
        :alt='key'
        @click='onView(index)'>
      </div>
	  </div>
	</div>
</template>

<script>
export default {
  data() {
    return {
      offsetLeft: "", // Смещение картинки
      widthImages: 120, // Ширина картинки в карусели
      index: 0, // Индекс картинки
      isActive: true, // Флаг для класса active в теге img
      path: "src/assets/img/", // Путь до папки с изображениями
      arrayNamesImages: [
        "1.jpg",
        "2.jpg",
        "3.jpg",
        "4.jpg",
        "5.jpg",
        "6.jpg",
        "7.jpg",
        "8.jpg",
        "9.jpg",
        "10.jpg"
      ], // Массив имен картинок
      arrayPathsImages: [] // Массив путей до картинок
    };
  },
  beforeMount() {
    for (let i = 0; i < this.arrayNamesImages.length; i++) {
      if (i == 0) {
        this.arrayPathsImages.push({
          img: this.path + this.arrayNamesImages[i],
          status: true
        });
      } else {
        this.arrayPathsImages.push({
          img: this.path + this.arrayNamesImages[i],
          status: false
        });
      }
    }
  },
  methods: {
    prevHendler() {
      this.arrayPathsImages[this.index].status = false;
      this.index--;
      if (this.index >= 0) {
        this.arrayPathsImages[this.index].status = true;
      } else {
        this.index = this.arrayPathsImages.length - 1;
        this.arrayPathsImages[this.index].status = true;
      }

      if (this.index < this.arrayPathsImages.length - 3) {
        this.offsetLeft = `left: -${this.widthImages * this.index + -240}px;`;
      } else {
        this.offsetLeft = `left: -${this.widthImages *
          (this.arrayPathsImages.length - 5)}px;`;
      }
    },
    nextHendler() {
      this.arrayPathsImages[this.index].status = false;
      this.index++;
      if (this.index < this.arrayPathsImages.length) {
        this.arrayPathsImages[this.index].status = true;
      } else {
        this.index = 0;
        this.arrayPathsImages[this.index].status = true;
      }

      if (this.index > 2 && this.index < this.arrayPathsImages.length - 2) {
        this.offsetLeft = `left: -${this.widthImages * this.index + -240}px;`;
      } else if (this.index == 0) {
        this.offsetLeft = `left: -${this.widthImages * this.index}px;`;
      }
    },
    onView(index) {
      this.index = index;
      for (let i = 0; i < this.arrayPathsImages.length; i++) {
        this.arrayPathsImages[i].status = false;
      }
      this.arrayPathsImages[this.index].status = true;

      if (this.index > 2 && this.index < this.arrayPathsImages.length - 2) {
        this.offsetLeft = `left: -${this.widthImages * this.index + -240}px;`;
      } else if (
        this.index > 2 &&
        this.index < this.arrayPathsImages.length - 1
      ) {
        this.offsetLeft = `left: -${this.widthImages * this.index + -360}px;`;
      } else if (this.index == 2) {
        this.offsetLeft = `left: -${this.widthImages * 0}px;`;
      } else if (this.index == 1) {
        this.offsetLeft = `left: -${(this.widthImages = 0)}px;`;
        this.widthImages = 120;
      }
    }
  }
};
</script>

<style lang='scss'>
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
      border-right: 3px solid #fff;
      border-left: 3px solid #fff;
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