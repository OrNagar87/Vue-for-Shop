<template>
  <div class="home">
    <div class="app">
      <h1>App</h1>
      <Header />
      <Products />
    </div>
  </div>
</template>
<script>
import Header from "../components/Header";
import Products from "../components/Products";

export default {
  name: "App",
  components: {
    Header,
    Products,
  },
};
</script>
<style>
.app {
  color: green;
  border: 4px groove green;
}
</style>
