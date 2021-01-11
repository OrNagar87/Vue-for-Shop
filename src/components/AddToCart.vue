<template>
  <button class="addbutton">ADD TO CART</button>
</template>

<script>
export default {
  props: ["id"],
};
</script>

<style>
.addbutton {
  background-color: rgb(238, 188, 94); /* Green */
  border: none;
  color: white;
  padding: 10px 25px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 10px;
  margin: 4px 2px;
  cursor: pointer;
}
</style>
