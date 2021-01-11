<template>
  <div class="wraper">
    <section class="products" v-for="val in objects" :key="val.id" :id="val.id">
      <div class="product-card" v-if="val.category === selected">
        <div class="product-image">
          <router-link :to="`/about/${val.id}`">
            <img :src="val.image" alt="" />
          </router-link>
        </div>
        <div class="product-info">
          <h5>{{ val.title }}</h5>
          <h6>{{ val.price }}$</h6>
        </div>
        <div class="adding">
          <AddToCart @click="add(val.id)" :id="val.id" />
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import AddToCart from "./AddToCart";
export default {
  props: ["objects", "selected", "add"],
  components: {
    AddToCart,
  },
};
</script>

<style>
.adding {
  margin-top: -85px;
}
h1 {
  font-size: 28px;
  font-weight: 300;
}

h5 {
  font-weight: 500;
  line-height: 1.7em;
}

h6 {
  color: #666;
  font-size: 14px;
}

label {
  color: #666;
  font-size: 10px;
  font-weight: 500;
  line-height: 2em;
  text-transform: uppercase;
}
.wraper {
  display: flex;
  border: 1px solid silver;
  -ms-box-orient: horizontal;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -moz-flex;
  display: -webkit-flex;

  -webkit-flex-wrap: wrap;
  flex-wrap: wrap;
}

.product-card {
  border: 4px groove blue;
  padding: 10px;
  background-color: #fff;
  box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
  margin: 5px;
  width: 300px;
  height: 300px;

  background-color: #fff;
  box-shadow: 0px 0px 11px 0px rgba(0, 0, 0, 0.25);
}

.product-image img {
  margin-left: auto;
  margin-right: auto;
  height: 180px;
  width: 180px;
}

.product-info {
  margin-top: auto;

  text-align: center;
}
</style>
