<template>
  <nav-bar />
  <router-view />
  <footer-page />
</template>


<script>
import NavBar from './components/NavBar.vue';
import FooterPage from './components/FooterPage.vue';

export default {
  components: {
    NavBar,
    FooterPage
  }
}
</script>

<style lang="scss">
* {
  margin: 0 auto;
  padding: 0;

}

// #app {
//   font-family: Avenir, Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
// }

// nav {
//   padding: 30px;

//   a {
//     font-weight: bold;
//     color: #2c3e50;

//     &.router-link-exact-active {
//       color: #42b983;
//     }
//   }
// }
</style>
