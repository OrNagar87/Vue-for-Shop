<template>
  <div class="app">
    <h1>App</h1>
    <Header />
    <Products />
  </div>
</template>

<script>
import Header from "./components/Header";
import Products from "./components/Products";

export default {
  name: "App",
  components: {
    Header,
    Products,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.app {
  color: green;
  border: 4px groove green;
}
</style>
