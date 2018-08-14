<template>
  <div>
    <h3>{{ beer.name }}</h3>
    <h1 class="text-base mt-10">{{ beer.description }}</h1>
  </div>
</template>

<script>
import axios from "axios";
// import BeerDetail from '~/components/BeerDetail.vue'

export default {
  data() {
    return {
      id: this.$route.params.id,
    };
  },
  async asyncData({ params, error }) {
    try {
      const { data } = await axios.get(
        `https://api.punkapi.com/v2/beers/${params.id}`
      );
      return {
        beer: data[0]
      };
    } catch (e) {
      error({ message: "User not found", statusCode: 404 });
    }
  }
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Bitter|Josefin+Sans");
@import url("https://fonts.googleapis.com/css?family=Lekton");
img {
  height: 500px;
  width: auto;
  margin: 0 auto;
  display: block;
}
h4 {
  font-family: "Lekton", sans-serif;
}
h1,
h3 {
  font-family: "Lekton", sans-serif;
}
</style>
