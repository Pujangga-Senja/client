<template>
  <div class="login mt-4">
    <div class="container">
      <div class="row d-flex justify-content-center">
        <div class="card col">
          <div class="card-header">Login</div>
          <form v-on:click.prevent>
            <div class="form-group">
              <label for="inputEmailLogin">Email address</label>
              <input
                v-model="userLoginData.email"
                type="email"
                class="form-control"
                id="inputEmailLogin"
                aria-describedby="emailHelp"
                placeholder="Enter email"
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
              />
            </div>
            <!-- <div class="form-group form-check">
              <input type="checkbox" class="form-check-input" id="exampleCheck1" />
              <label class="form-check-label" for="exampleCheck1">Check me out</label>
            </div>-->
            <button
              v-on:click="$emit('userLogin', userLoginData)"
              type="submit"
              class="btn btn-primary"
            >Submit</button>
          </form>
        </div>

        <div class="card col">
          <div class="card-header">Register</div>
          <form>
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
            <!-- <div class="form-group form-check">
              <input type="checkbox" class="form-check-input" id="exampleCheck1" />
              <label class="form-check-label" for="exampleCheck1">Check me out</label>
            </div>-->
            <button v-on:click="$emit('userRegister', userRegisterData)">Submit</button>
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
      }
    };
  }
};
</script>

<style></style>