<template>
  <div class="wrapper">
    <div class="top_nav">
        <div class="left">
          <div class="logo"><p><span>Gaming</span>Market</p></div>
          <div class="search_bar">
              <input type="text" placeholder="Search">
          </div>
      </div> 
      <div class="right">
        <ul>
          <li>
            <router-link to="/registration">Registration</router-link>
          </li>
          <li>
            <router-link to="/login">Login</router-link>
          </li>
          <li>
            <router-link to="/contact">Contact Us</router-link>
          </li>
        </ul>
      </div>
    </div>
    <div class="bottom_nav" :class="{ 'sticky': isSticky }">
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">Profile</a></li>
        <li><a href="#">Writing</a></li>
        <li><a href="#">Design</a></li>
        <li><a href="#">Marketing</a></li>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Map</a></li>
        <li><a href="#">Articles</a></li>
      </ul>
  </div>
  
  <div class="banner">
    <img src="https://i.postimg.cc/4ymwDgqT/Screenshot-2023-03-10-135339.png" alt="banner_img">
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      isSticky: false,
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      const topNavHeight = this.$el.querySelector('.top-nav').offsetHeight;
      if (window.pageYOffset > topNavHeight) {
        this.isSticky = true;
      } else {
        this.isSticky = false;
      }
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Josefin+Sans|Mountains+of+Christmas&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none;
  text-decoration: none;
  font-family: "Josefin Sans", sans-serif;
}

.wrapper .multi_color_border{
  width: 100%;
  height: 5px;
  background: linear-gradient(to right, #37a000 0% , #37a000 25%, #494949 25%, #494949 50%, #37a000 50%, #37a000 75%, #494949 75%, #494949 100%);
}

.wrapper .top_nav{
  margin-top: 5px;
  width: 100%;
  height: 65px;
  background: black;
  padding: 0 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.wrapper .top_nav .left{
  display: flex;
  align-items: center;
}

.wrapper .top_nav .left .logo p{
  font-size: 24px;
  font-weight: bold;
  color: #494949;
  font-family: "Mountains of Christmas", cursive;
  margin-right: 25px;
}

.wrapper .top_nav .left .logo p span{
  color: #37a000;
  font-family: "Mountains of Christmas", cursive;
}

.wrapper .top_nav .left .search_bar input[type="text"]{
  border: 1px solid #666666;
  padding: 5px 10px; 
  outline: none;
  transition: all 0.5s linear;
}

.wrapper .top_nav .left .search_bar input[type="text"]:focus{
  width: 250px;
}

.wrapper .top_nav .right ul{
  display: flex;
}

.wrapper .top_nav .right ul li{
  margin: 0 12px;
}

.wrapper .top_nav .right ul li:hover{
  color: red;
}

.wrapper .top_nav .right ul li a{
  display: block;
  padding: 8px 10px;
  color: white;
}

.wrapper .bottom_nav{
  width: 100%;
  background: black;
  height: 45px;
  padding: 0 50px;
}

.wrapper .bottom_nav ul{
  width: 100%;
  height: 45px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.wrapper .bottom_nav ul li a{
  color: white;
  letter-spacing: 2px;
  text-transform: uppercase;
  font-size: 12px;
}

.wrapper .banner img{
  width: 100%;
  height: 400px;
}
</style>

