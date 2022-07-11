<template>
  <Header /><br/><br/><br/><br/>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/login">Login</router-link> |
    <router-link to="/subs">Subs</router-link>
  </nav>
  <router-view/>
</template>

<script>
  import Card from "./components/Card.vue"
  import CardInfo from "./components/CardInfo.vue"
  import Header from "./components/Header.vue"
  import UserInfo from "./components/UserInfo.vue"
  export default {
    components: {
      Card,
      CardInfo,
      Header,
      UserInfo
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #ececec;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

</style>
