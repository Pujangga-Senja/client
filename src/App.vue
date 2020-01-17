<template>
  <div id="app">
    <Header v-on:userLogout="logout" v-bind:isUserLogin="isUserLogin"></Header>
    <Login v-show="!isUserLogin" v-on:userLogin="login" v-on:userRegister="register"></Login>
    <AudioForm v-show="isUserLogin" v-on:textResult="getText" v-show="isUserLogin"></AudioForm>
    <Content v-show="isUserLogin"></Content>
    <TextImage v-show="isUserLogin" v-if="imageUrl == ''" v-on:image-link="getImage" :textResult="textResult"></TextImage>
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
import AudioForm from './components/AudioForm'
// eslint-disable-next-line no-unused-vars
import axios from "axios";

export default {
  name: "app",
  data() {
    return {
      isUserLogin: false, // 0 --- login page, 1 --- content page
      imageUrl: "",
      errorStatus: null,
      textResult: ''
    };
  },
  components: {
    Header,
    Login,
    Content,
    Footer,
    TextImage,
    ImageResult,
    AudioForm
  },
  methods: {
    login(data) {
      axios
        .post("http://35.192.129.227/users/login", {
          email: data.email,
          password: data.password
        })
        .then(response => {
          console.log(response)
          localStorage.setItem("token", response.data.token);
          this.isUserLogin = true;
        })
        .catch(err => {
          this.errorStatus = err.response.status
          console.log(err.response.status)
        });
    },
    register(data) {
      axios
        .post("http://35.192.129.227/users/register", {
          email: data.email,
          password: data.password
        })
        .then(response => {
          console.log(response);

          return this.login(data);
        })
        .catch(err => console.log(Object.keys(err)));

      // kalau berhasil
      // this.isUserLogin = true;
    },
    logout() {
      localStorage.removeItem("token");
      this.imageUrl = ''
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
    },
    getText(val){
      this.textResult = val
    }
  },
  created: function(){
    if(localStorage.hasOwnValue('token')){
      this.isLogin = true
    }
  }
};
</script>

<style lang="css">
  body, html{
    height: 100%;
    width: 100%;
  }
  body{
    background-image: url('./assets/langit-senja.jpg');
    background-position: center;
    background-repeat: no-repeat;
  }
</style>
