<template>
  <div id="app">
    <div class="main-container">
      <h1 class="header-1">{{ this.items.name }}</h1>

      <figure class="squeeze-img-container">
        <img src="./assets/images/squeezing.png" alt="" />
      </figure>
      <nav class="navigation">
        <ul class="nav_list">
          <li class="nav_list_item"><a href="">Home</a></li>
          <li class="nav_list_item"><a href="">About</a></li>
          <li class="nav_list_item">
            <figure class="nav-img">
              <img src="./assets/images/lady.jpg" alt="a lady photo" />
            </figure>
          </li>
          <li class="nav_list_item"><a href="">Gallery</a></li>
          <li class="nav_list_item"><a href="">Contact</a></li>
        </ul>
      </nav>

      <ul class="social">
        <li class="social_item">
          <a href="social_link">
            <span class="figure">
              <img src="./assets/images/instagram.png" alt="instagram" />
            </span>
            <span class="social-item-title">{{
              this.items.social_media.instagram
            }}</span>
          </a>
        </li>
        <li class="social_item">
          <a href="">
            <span class="figure">
              <img src="./assets/images/twitter.png" alt="twitter" />
            </span>
            <span class="social-item-title">{{
              this.items.social_media.twitter
            }}</span>
          </a>
        </li>
        <li class="social_item">
          <a href="">
            <span class="figure">
              <img src="./assets/images/snapchat.png" alt="snapchat" />
            </span>
            <span class="social-item-title">{{
              this.items.social_media.snapchat
            }}</span>
          </a>
        </li>
        <li class="social_item">
          <a href="">
            <span class="figure">
              <img src="./assets/images/email.png" alt="email" />
            </span>
            <span class="social-item-title">{{
              this.items.social_media.email
            }}</span>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      items: null
    };
  },

  async created() {
    try {
      const res = await axios.get(`https://hirng-x2021.glitch.me/api`);
      this.items = res.data;

      console.log(this.items);
    } catch (err) {
      console.error(err);
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Hanalei+Fill&family=Nanum+Gothic&display=swap");

:root {
  --color-white: #f7f0f0;
  --link-hover-color: #5c5959;
}

/*** Rest and Normalization**/
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

body {
  box-sizing: border-box;
  font-family: "Nanum Gothic", sans-serif;
}

ul li {
  list-style-type: none;
}

a {
  text-decoration: none;
}

/***main container styles**/
.main-container {
  position: relative;
  padding: 10px;
  background: linear-gradient(
    to right,
    #bd0f4d 0%,
    #bd0f4d 50%,
    #cb2964 50%,
    #cb2964 100%
  );

  height: auto;
}

/***header styles**/
.header-1 {
  text-transform: uppercase;
  font-size: 2.5rem;
  color: var(--color-white);
  letter-spacing: 1.5rem;
  text-align: center;
  margin: 2.5rem 0;
}

/***centered Image styles**/
figure.squeeze-img-container {
  box-shadow: rgba(0, 0, 0, 0.35) -4px 5px 30px;
  background-color: #bd0f4d;
  width: 580px;
  height: 600px;
  margin: 0 auto;
  position: relative;
}

figure.squeeze-img-container img {
  width: auto;
  /* height: 100%; */
  height: 35rem;
  display: inline-block;
  position: absolute;
  bottom: 0;
  left: -5rem;
}

/**Social media contact style***/
.social {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: flex-start;
  z-index: 9;
  position: absolute;
  right: 2.5rem;
  top: 25%;
  height: 20rem;
}
.social li a {
  display: flex;
  justify-content: space-around;
  /* flex-wrap: wrap; */
  align-items: center;
  color: var(--color-white);
}
.social li a:hover .social-item-title {
  color: var(--link-hover-color);
}

.social li a span img {
  width: 1.55rem;
}

span.figure {
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  padding: 0.25rem 0.5rem;
  background-color: var(--color-white);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-right: 10px;
  border-radius: 5px;
}

.social-item-title {
  letter-spacing: 1.5px;
  font-size: 1rem;
}

/***footer navigation styles**/
.navigation {
  max-width: 80%;
  margin-left: auto;
  margin-right: auto;

  margin-top: 2.5rem;
  margin-bottom: 2.5rem;
}

.nav_list {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  margin-left: 6rem;

  max-width: 100%;
}
.nav_list_item .nav-img {
  width: 7rem;
  height: 7rem;
}
.nav_list_item .nav-img img {
  max-width: 100%;
  border-radius: 50%;
}

.nav_list_item a {
  text-transform: uppercase;
  color: var(--color-white);
  font-weight: 550;
  letter-spacing: 10px;
  font-size: 1.5rem;
}
</style>
