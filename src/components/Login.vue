<template>
  <div class="login mt-4">
    <div class="container">
      <div class="row d-flex justify-content-center">
        <!-- Login -->
        <div class="card col" v-show="login" id="loginPage">
          <div class="card-header text-center">Login</div>
          <form v-on:click.prevent>
            <div class="form-group">

              <div class="alert alert-danger" role="alert" v-if="errorStatus">
                Invalid email or password
              </div>

              <label for="inputEmailLogin">Email address</label>
              <input
                v-model="userLoginData.email"
                type="email"
                class="form-control"
                id="inputEmailLogin"
                aria-describedby="emailHelp"
                placeholder="Enter email"
                required
              />
              <small
                id="emailHelp"
                class="form-text text-muted"
              >We'll never share your email with anyone else.</small>
            </div>
            <div class="form-group">
              <label for="inputPasswordLogin">Password</label>
              <input
                v-model="userLoginData.password"
                type="password"
                class="form-control"
                id="inputPasswordLogin"
                placeholder="Password"
                required
              />
            </div>
            <button
              v-on:click="$emit('userLogin', userLoginData)"
              type="submit"
              class="btn btn-primary"
            >Submit</button>
            <h5>Need an account?</h5>
            <a href="#" id="btn-register" @click="register = true, login = false">Register here</a>
            <!-- <div class="g-signin2 btn" v-on:click="onSignIn"></div> -->
          </form>
        </div>

        <!-- Register -->
        <div class="card col" v-show="register" id="registerPage">
          <div class="card-header text-center">Register</div>
          <form v-on:click.prevent>
            <!-- email -->
            <div class="form-group">
              <label for="inputEmailRegister">Email address</label>
              <input
                v-model="userRegisterData.email"
                type="email"
                class="form-control"
                id="inputEmailRegister"
                aria-describedby="emailHelp"
                placeholder="Enter email"
              />
              <small
                id="emailHelp"
                class="form-text text-muted"
              >We'll never share your email with anyone else.</small>
            </div>

            <!-- password -->
            <div class="form-group">
              <label for="inputPasswordRegister">Password</label>
              <input
                v-model="userRegisterData.password"
                type="password"
                class="form-control"
                id="inputPasswordRegister"
                placeholder="Password"
              />
            </div>
            <button
              v-on:click="$emit('userRegister', userRegisterData)"
              type="submit"
              class="btn btn-primary"
            >Submit</button>
            <h5>or already have an account?</h5>
            <a href="#" id="btn-login" @click="login = true, register = false">Login here</a>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  data: function() {
    return {
      userLoginData: {
        email: "",
        password: ""
      },
      userRegisterData: {
        email: "",
        password: ""
      },
      register: false,
      login: true,
    };
  },
  props: ['errorStatus']
};
</script>

<style scoped>
  .col {
    padding: 20px;
    background-color:  rgba(34, 47, 62,0.5);
    color: white;
  }

  .card-header {
    font-size: 24px;
    font-weight: 500;
    margin-bottom: 20px;
  }

  #btn-register, #btn-login {
    color: white;
    font-size: 18px;
  }

  .btn {
    margin-bottom: 15px
  }
</style>