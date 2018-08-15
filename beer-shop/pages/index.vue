<template>

<div></div>
</template>

<script>
import axios from "axios";
import Logo from "@/components/Logo.vue";
import ListBeer from "@/components/ListBeer.vue";

export default {
  components: {
    Logo,
    ListBeer,
  },

};
</script>

<style>
.container {
}
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
.links {
  padding-top: 15px;
}
#search {
  width: 100%;
  font-size: 16px;
  padding: 12px 20px 12px 40px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
#listBeer {
  list-style-type: none;
  padding: 0;
  margin: 0;
  color: black;
  display: block;
  font-size: 18px;
  padding: 12%;
}
.listdetail {
  font-family: "Bitter", serif;
}
.list {
  font-family: "Lekton", sans-serif;
}
li:hover {
  border: 2px dotted black;
}
</style>
