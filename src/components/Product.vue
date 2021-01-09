<template>
  <div class="wrapper">
    <section class="products" v-for="val in objects" :key="val.id">
      <div class="product-card" v-if="val.category === selected">
        <div class="product-image">
          <img :src="val.image" alt="" />
        </div>
        <div class="product-info">
          <h5>{{ val.title }}</h5>
          <h6>{{ val.price }}</h6>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  props: ["objects", "selected"],
};
</script>

<style>
ul {
  list-style: none;
}
section {
  display: none;
}
h1 {
  font-size: 28px;
  font-weight: 300;
  flex: 1;
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

.products {
  display: flex;
  flex-wrap: wrap;
}
.wrapper {
}

.product-card {
  border: 4px groove blue;
  display: flex;
  flex-direction: column;
  padding: 2%;
  flex: 1 16%;

  background-color: #fff;
  box-shadow: 0px 0px 11px 0px rgba(0, 0, 0, 0.25);
}

.product-image img {
  display: block;
  margin-left: auto;
  margin-right: auto;
  height: 180px;
  width: 180px;
}

.product-info {
  margin-top: auto;
  padding-top: 20px;
  text-align: center;
}
</style>
