<template>
  <input
    class="mt-10 ml-10"
    id="search"
    type="text"
    placeholder="Search for name"
    v-model="textSearch"
    @keyup.enter="search"
    v-on:input="debounceInput"

  >
</template>

<script>
import axios from 'axios'
import _ from 'lodash'

  export default {
    data() {
      return {
        textSearch: '',


      }
    },
    // directive: {debounce},
    watch: {
      textSearch(val) {

          // setTimeout(this.search(val),500);
          this.search(val);
      }
    },
    methods: {
      async search(text) {
        try {
          const {data} =  await axios.get('https://api.punkapi.com/v2/beers?beer_name=' + text)
          this.$emit('searchChange', data)
        } catch (error) {
          console.log(error)
        }
      },
      debounceInput: _.debounce (function(e)  {

            this.textSearch = e.target.value;
      }, 2000)
    },
  }
</script>

<style >

</style>
