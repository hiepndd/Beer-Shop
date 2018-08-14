<template>
  <input
    class="mt-10 ml-10"
    id="search"
    type="text"
    placeholder="Search for name"
    v-model="textSearch"
    @keyup.enter="search"
  >
</template>

<script>
import axios from 'axios'
import debounce from 'lodash/debounce'

  export default {
    data() {
      return {
        textSearch: '',
      }
    },
    watch: {
      textSearch(val) {
        debounce(this.search(val), 500)
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
      }
    },
  }
</script>

<style scoped>

</style>
