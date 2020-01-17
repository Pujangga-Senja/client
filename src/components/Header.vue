<template>
  <header>
    <nav class="navbar navbar-dark bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand">Pujangga Senja</a>
        <form v-on:click.prevent v-show="isUserLogin" class="form-inline">
          <button
            v-on:click="$emit('userLogout')"
            class="btn btn-outline-success my-2 my-sm-0"
            type="submit"
          >Logout</button>
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

<style lang="css" scoped>
  header nav{
    background-color: rgba(34, 47, 62,0.5) !important;
  }

  header nav a {
    color: white !important;
    font-weight: 800;
    font-size: 28px;
  }
</style>