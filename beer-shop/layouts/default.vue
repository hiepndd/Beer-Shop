<template>
  <div class="font-sans">
    <div class="container mx-auto px-4">
      <div class="-mx-4 flex">
        <div class="w-1/3 px-4">
          <list-beer/>
        </div>
        <div class="w-2/3 px-4">
          <nuxt/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ListBeer from "@/components/ListBeer.vue";

export default {
  components: {
    ListBeer
  }
}
</script>

<style>
html
{
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}
*, *:before, *:after
{
  box-sizing: border-box;
  margin: 0;
}
</style>
