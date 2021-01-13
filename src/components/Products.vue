<template>
  <div class="our_products">
    <h1>Our Products</h1>
    <nav class="product-filter">
      <div class="sort">
        <div class="collection-sort">
          <label>Filter by:</label>
          <select v-model="selected">
            <option
              v-for="category in categories"
              :value="category"
              :key="category"
            >
              {{ category }}
            </option>
          </select>
        </div>
      </div>
      <button class="remove_item" @click="removeLastItem()">remove item</button>
      <div class="cart">Cart Quantity:{{ cart }}</div>
    </nav>
    <Product :objects="objects" :selected="selected" :add="AddCart" />
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import axios from "axios";
// eslint-disable-next-line no-unused-vars
import VueAxios from "vue-axios";
import Product from "./Product";

export default {
  data() {
    return {
      selected: "all",
      objects: [],
      cart: 0,
    };
  },
  components: {
    Product,
  },
  methods: {
    removeLastItem() {
      this.objects.splice(this.objects.length - 1);
      alert("remove");
    },
    AddCart(id) {
      this.cart++;

      console.log("adding" + this.objects[id].title);
    },
  },

  computed: {
    categories() {
      const groupBy = (xs, key) =>
        xs.reduce((rv, x) => {
          rv[x[key]] = true || [];
          return rv;
        }, {});
      return Object.keys(groupBy(this.objects, "category", "id"));
    },
  },
  mounted() {
    axios.get("https://fakestoreapi.com/products").then((resp) => {
      this.objects = resp.data;
      console.log(resp.data);
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cart {
  border: 3px groove rgb(199, 108, 199);
  margin: 10px;
  padding: 5px;
  width: 180px;
}
.our_products {
  border: 4px groove orange;
  color: black;
}
.product-filter {
  padding: 10px 0;
}
.remove_item {
  float: right;
  width: 180px;
  margin: 10px;
  padding: 5px;
}

.sort {
}

.collection-sort {
}

.collection-sort:first-child {
  padding-right: 20px;
}

label {
  color: #666;
  font-size: 10px;
  font-weight: 500;
  line-height: 2em;
  text-transform: uppercase;
}
</style>
