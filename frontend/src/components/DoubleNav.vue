<template>
  <div class="container">
    <div class="top_nav">
    <ul>
      <router-link to="/">Home</router-link>
      <router-link to="/products">Products</router-link>
      <router-link to="/Admin">Admin</router-link>
      <router-link to="/about">About Us</router-link>
      <router-link to="/contact">Contact Us</router-link>
      <router-link to="/registration">Registration</router-link>
      <router-link to="/login">Login</router-link>
    </ul>
  </div>
  <div class="nav-container">
    <div class="bottom_nav">
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
</div>
  </div>
<!-- </div> -->
<section>
  
</section>
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

/*.wrapper .multi_color_border{
  width: 100%;
  height: 5px;
  background: linear-gradient(to right, #37a000 0% , #37a000 25%, #494949 25%, #494949 50%, #37a000 50%, #37a000 75%, #494949 75%, #494949 100%);
}*/
.nav-container{
  position: absolute;
  width: 100%;
  height: 100%;
}
.bottom_nav{
  margin-top: 0px;
  width: 100%;
  height: 65px;
  background: grey;
  padding: 0 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: sticky;
  top: 0;
}

.bottom_nav .left{
  display: flex;
  align-items: center;
}

.bottom_nav .left .logo p{
  font-size: 24px;
  font-weight: bold;
  color: #494949;
  font-family: "Mountains of Christmas", cursive;
  margin-right: 25px;
}

.bottom_nav .left .logo p span{
  color: #37a000;
  font-family: "Mountains of Christmas", cursive;
}

.bottom_nav .left .search_bar input[type="text"]{
  border: 1px solid #666666;
  padding: 5px 10px; 
  outline: none;
  transition: all 0.5s linear;
}

.bottom_nav .left .search_bar input[type="text"]:focus{
  width: 250px;
}

.bottom_nav .right ul{
  display: flex;
}

.bottom_nav .right ul li{
  margin: 0 12px;
}

.bottom_nav .right ul li:hover{
  color: red;
}

.bottom_nav .right ul li a{
  display: block;
  padding: 8px 10px;
}

.top_nav{
  width: 100%;
  background: black;
  height: 45px;
  padding: 0 50px;
  
}

.top_nav :hover{
  color: green;
}

.top_nav ul{
  width: 100%;
  height: 45px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
}

.top_nav ul li a{
  color: white;
  letter-spacing: 2px;
  text-transform: uppercase;
  font-size: 12px;
}

.banner img{
  width: 100%;
  height: 400px;
}
</style>

