<template>
  <nav id="nav">
    <router-link :class="{active:$route.name === 'Home'}" to="/">Home </router-link>  
    <router-link :class="{active:$route.name === 'Cart'}" to="/cart"> Cart</router-link>
  </nav>
  <router-view/>
</template>

<script>
  export default {
    mounted() {
      this.$store.commit('updateCartFromLocalStorage');
    }
  }
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

html, body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

body {
  background-color: black(245,245,245);
}

#nav {
  padding: 1rem;
  width: 100%;
  height: 3rem;
  background-color: black;
  line-height: 3rem;

  a {
    font-weight: bold;
    color: grey;
    text-decoration: none;
    margin: 0, 5px, 0 5px;
    font-size: 1.25rem;

    &.active{
      color: #78B1BF;
    }
  }
}
.text-center {
 text-align: center;
}
</style>
