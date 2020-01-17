<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" />
    <h1>{{ count }}</h1>
    <HelloWorld v-on:add-count="addCounter" v-bind:msg="message" />-->
    <Header v-bind:isUserLogin="isUserLogin"></Header>
    <Login v-show="!isUserLogin" v-on:userLogin="login" v-on:userRegister="register"></Login>
    <Content v-show="isUserLogin"></Content>
    <TextImage v-show="isUserLogin" v-if="imageUrl == ''" v-on:image-link="getImage"></TextImage>
    <ImageResult :imageUrl="imageUrl" v-if="imageUrl != ''"></ImageResult>
    <Footer></Footer>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld";
import Header from "./components/Header";
import Login from "./components/Login";
import Content from "./components/Content";
import Footer from "./components/Footer";
import TextImage from "./components/TextImage"
import ImageResult from "./components/ImageResult"

export default {
  name: "app",
  data() {
    return {
      isUserLogin: false, // 0 --- login page, 1 --- content page
      message: "Hi, Markus!",
      count: 0,
      imageUrl: ''
    };
  },
  components: {
    Header,
    Login,
    Content,
    Footer,
    TextImage,
    ImageResult
  },
  methods: {
    addCounter(increment, thres) {
      // this.count = thres;
      if (this.count > thres) {
        this.count = 0;
      } else {
        this.count += increment;
      }
    },
    login(data) {
      // eslint-disable-next-line no-console
      console.log(data);

      // kalau berhasil
      this.isUserLogin = true;
    },
    register(data) {
      // eslint-disable-next-line no-console
      console.log(data);

      // kalau berhasil
      this.isUserLogin = true;
    },
    getImage(val){
      console.log(val)
      this.imageUrl = val
    }
  }
};
</script>

<style>
/* #app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
