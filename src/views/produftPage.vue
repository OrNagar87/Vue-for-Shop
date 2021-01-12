<template>
  <div>
    productPage
    <img class="pimg" :src="ourproduct.image" alt="" />
    <div class="product-info">
      <h2>{{ ourproduct.title }}</h2>
      <h3>{{ ourproduct.price }}$</h3>
      <h4>{{ ourproduct.description }}</h4>
    </div>
    <AddToCart />
  </div>
</template>

<script>
import axios from "axios";
import AddToCart from "../components/AddToCart";
export default {
  props: ["id"],
  components: {
    AddToCart,
  },
  data() {
    return {
      ourproduct: {},
    };
  },
  computed: {},

  mounted() {
    axios.get("https://fakestoreapi.com/products").then((resp) => {
      console.log(resp.data);
      var index = this.$route.params;
      console.log(resp.data[index.id]);
      this.ourproduct = resp.data[index.id - 1];
    });
  },
};
</script>

<style>
.pimg {
  height: 200px;
  margin-left: 40%;
  display: block;
  -webkit-transform: scale(1);
  transform: scale(1);
  -webkit-transition: 0.3s ease-in-out;
  transition: 0.3s ease-in-out;
}
.pimg:hover {
  -webkit-transform: scale(1.3);
  transform: scale(1.3);
}
</style>
