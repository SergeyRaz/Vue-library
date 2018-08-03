<template>
	<div class='menu'>
    <div class="container">
      <nav>
        <div class="nav-item"><a href="#">Link - 1</a></div>
        <div class="nav-item"><a href="#">Link - 2</a></div>
        <div class="nav-item"><a href="#">Link - 3</a></div>
        <div class="nav-item"><a href="#">Link - 4</a></div>
        <div class="nav-item"><a href="#">Link - 5</a></div>
        <div class="nav-btn"><a href="#"><i class="fa fa-bars" aria-hidden="true"></i></a></div>
      </nav>
    </div>
	</div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {}
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
.menu {
  color: #222;
  .container {
    max-width: 1200px;
    padding: 0px;
    margin: 0 auto;
    nav {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      background-color: darkcyan;
      @media screen and (max-width: 768px) {
        background-color: transparent;
      }
      .nav-item {
        border-right: 1px solid #fff;
        background-color: darkcyan;
        @media screen and (max-width: 768px) {
          display: none;
        }
        &:hover {
          background-color: #008686;
        }
        a {
          padding: 8px 30px;
          color: #fff;
          display: block;
          text-shadow: 1px 1px 3px #000;
        }
      }
      .nav-btn {
        margin-left: auto;
        display: none;
        padding: 3px 10px;
        
        @media screen and (max-width: 768px) {
          display: block;
        }
        a {
          color: darkcyan;
          font-size: 26px;
          svg {
            stroke-width: 3px;
            stroke: #000;
          }
        }
      }
    }
  }
}
</style>