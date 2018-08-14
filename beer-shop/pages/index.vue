<template>
  <div class="container mx-auto max-w-full">
   <div class="flex">
    <div class="container w-1/3 list" >
      <ListBeer/>

    </div>
    <div class="container mx-auto w-2/3 mt-20 listdetail">
           <div class="ml-10">
            <h1><nuxt-child :key="$route.params.id"/></h1>
           </div>
    </div>
   </div>
  </div>
</template>

<script>
import axios from 'axios'
import Logo from '~/components/Logo.vue'
import ListBeer from '~/components/ListBeer.vue'
import BeerDetail from '~/components/BeerDetail.vue'

export default {

  components: {
    Logo,
    ListBeer,
    BeerDetail,
  },

  data() {
    return {
      listBeer: [],
      textSearch: '',
      select: '',
    }
  },

  methods: {
  search(){
       axios.get('https://api.punkapi.com/v2/beers?beer_name=' + this.textSearch).then(response => {
         this.listBeer = response.data
         if (this.listBeer.length === 0){document.getElementById('error').innerHTML = 'No Results Found'}
         else {document.getElementById('error').innerHTML = ' '}
       })
  },


  }


}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Bitter|Josefin+Sans');
@import url('https://fonts.googleapis.com/css?family=Lekton');
.container
{

}
.title
{
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
.subtitle
{
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
.links
{
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
  font-family: 'Bitter', serif;
}
.list {
  font-family: 'Lekton', sans-serif;
}
li:hover{
  border: 2px dotted black;
}


</style>
