<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>

import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Main,
    Header,
  },
};
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  // per gli occhi
  background-color: rgb(6, 11, 43);
  color: white;
}
</style>
