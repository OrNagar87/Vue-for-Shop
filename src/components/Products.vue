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
    </nav>

    <Product :objects="objects" :selected="selected" />
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
      selected: "men clothing",
      objects: [],
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
  },
  computed: {
    categories() {
      const groupBy = (xs, key) =>
        xs.reduce((rv, x) => {
          rv[x[key]] = true || [];
          return rv;
        }, {});
      return Object.keys(groupBy(this.objects, "category"));
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
.our_products {
  border: 4px groove orange;
  color: black;
}
.product-filter {
  display: flex;
  padding: 30px 0;
}
.remove_item {
  display: flex;
  float: right;
}

.sort {
  display: flex;
  align-self: flex-end;
}

.collection-sort {
  display: flex;
  flex-direction: column;
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
