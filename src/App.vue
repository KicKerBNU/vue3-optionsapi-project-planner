<template>
  <NavBar></NavBar>
  <div class="nav-margin"></div>
  <router-view/>
</template>

<script>
import NavBar from "./components/Navbar.vue";

export default {
  components:  { NavBar }
}
</script>

<style>
body{
  background: #f2f2f2;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: #555;
}
.nav-margin{
  margin-top: 72rem;
}
:root {
    --color-1: #00ce89 !important;
}

</style>
