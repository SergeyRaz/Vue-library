<template>
	<div class='popup'>
		<div class="popup-btn" @click="showHendler"><i class="far fa-envelope"></i></div>
		<div class="popup-block" :class="{active : isActive}">Lorem ipsum dolor sit amet consectetur 
			adipisicing elit. Temporibus provident aliquid asperiores animi veritatis? 
			Tenetur optio velit quas porro vitae.
			<div class="corner">
				<div class="corner2"></div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
  data() {
    return {
      isActive: false
    };
  },
  methods: {
    showHendler() {
      this.isActive = !this.isActive;
    }
  }
};
</script>

<style lang='scss'>
* {
  padding: 0;
  margin: 0;
  list-style: none;
  box-sizing: border-box;
  text-decoration: none;
  font-family: Roboto, sans-serif;
}
.popup {
  position: absolute;
  left: 55%;
  top: 30%;
  .popup-btn {
    font-size: 26px;
    color: #ccc;
    cursor: pointer;
    display: inline-block;
    svg {
      transition: 0.2s ease-out;
    }
    &:hover {
      // color: #888;
      svg {
        transform: scale(1.5);
      }
    }
  }
  .popup-block {
    user-select: none;
    width: 320px;
    box-shadow: 0 0 15px #fff;
    border: 1px solid #ddd;
    padding: 10px;
    border-radius: 5px;
    background-color: #fdfdfd;
    position: absolute;
    top: -5px;
    right: 45px;
    display: none;
    opacity: 0;
    .corner {
      border: 10px solid transparent;
      border-left: 10px solid #ddd;
      position: absolute;
      right: -20px;
      top: 10px;
      .corner2 {
        border: 9px solid transparent;
        border-left: 9px solid #fdfdfd;
        position: absolute;
        right: -8px;
        top: -9px;
      }
    }
  }
  .active {
		animation: anim-opacity .3s linear forwards;
    display: block;
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