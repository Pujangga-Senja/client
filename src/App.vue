<template>
  <div id="app">
    <Header v-on:userLogout="logout" v-bind:isUserLogin="isUserLogin"></Header>
    <Login v-show="!isUserLogin" v-on:userLogin="login" v-on:userRegister="register"></Login>
    <Content v-show="isUserLogin"></Content>
    <TextImage v-show="isUserLogin" v-if="imageUrl == ''" v-on:image-link="getImage"></TextImage>
    <ImageResult :imageUrl="imageUrl" v-if="imageUrl != ''"></ImageResult>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from "./components/Header";
import Login from "./components/Login";
import Content from "./components/Content";
import Footer from "./components/Footer";
import TextImage from "./components/TextImage";
import ImageResult from "./components/ImageResult";
// eslint-disable-next-line no-unused-vars
import axios from "axios";

export default {
  name: "app",
  data() {
    return {
      isUserLogin: false, // 0 --- login page, 1 --- content page
      imageUrl: ""
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
    login(data) {
      axios
        .post("http://localhost:3000/users/login", {
          email: data.email,
          password: data.password
        })
        .then(response => {
          localStorage.setItem("token", response.data.token);
          this.isUserLogin = true;
        })
        .catch(err => console.error(err));
    },
    register(data) {
      console.log(data);

      // kalau berhasil
      this.isUserLogin = true;
    },
    logout() {
      localStorage.removeItem("token");
      this.isUserLogin = false;
    },
    beforeCreate() {
      const token = localStorage.getItem("token");

      if (!token) {
        this.isUserLogin = false;
      } else {
        this.isUserLogin = true;
      }
    },
    getImage(val) {
      console.log(val);
      this.imageUrl = val;
    }
  }
};
</script>

<style>
</style>
