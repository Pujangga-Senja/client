<template>
  <header>
    <nav class="navbar navbar-light bg-light">
      <div class="container">
        <a class="navbar-brand">Pujangga Senja</a>
        <form v-show="isUserLogin" class="form-inline">
          <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Logout</button>
        </form>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
  data: function() {
    return {};
  },
  props: {
    isUserLogin: Boolean
  }
};
</script>

<style></style>