<template>
  <div>
    productPage
    <div class="ifID" v-if="ourproduct">
      <img class="pimg" :src="ourproduct.image" alt="" />
      <div class="product-info">
        <h2>{{ ourproduct.title }}</h2>
        <h3>{{ ourproduct.price }}$</h3>
        <h4>{{ ourproduct.description }}</h4>
      </div>
      <AddToCart />
    </div>
    <div v-else>
      המוצר לא נמצא במערכת אנא חזור לדף הבית ובחר מוצר
    </div>
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
    axios
      .get("https://fakestoreapi.com/products/" + this.$route.params.id)
      .then((resp) => {
        console.log(resp.data);
        this.ourproduct = resp.data;
      });
  },
};
</script>

<style>
.pimg {
  height: 200px;
  width: 200px;
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
