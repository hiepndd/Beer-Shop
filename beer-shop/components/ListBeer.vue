<template>
   <div>
     <input class="mt-10 ml-10" id="search" type="text" placeholder="Search for name" v-model="textSearch" @keyup.enter="search" >
       <ul id="listBeer" class="list">
        <li  v-for="beer in  listBeer" :key="beer.id" @click="select=beer">
          <nuxt-link class="no-underline text-black" :to="`/${beer.id}`" :listBeer="listBeer">
            {{ beer.name }}
          </nuxt-link>
        </li>

       </ul>
   </div>
</template>
<script>
import axios from 'axios'
export default {

 data() {
    return {
       listBeer: [],
     searchResult: [],
     textSearch: '',
      select: '',
    }
  },
  created(){
    axios.get(`https://api.punkapi.com/v2/beers`)
    .then (response =>{
      this.listBeer = response.data,
      this.searchResult = this.listBeer
    })
  },
 methods: {
  search(){
       axios.get('https://api.punkapi.com/v2/beers?beer_name=' + this.textSearch).then(response => {
         this.listBeer = response.data
        //  if (this.listBeer.length === 0){document.getElementById('error').innerHTML = 'No Results Found'}
        //  else {document.getElementById('error').innerHTML = ' '}
        if (this.listBeer.length == 0){
          this.listBeer = this.searchResult;
        }
       })
  },

 },
 watch: {
   textSearch: 'search',

 },
//  computed: {
//    filteredNames(){
//      let filter = this.textSearch;
//      this.searchResult = this.listBeer.filter(item => item.name.toUpperCase().includes(filter.toUpperCase()))
//      return searchResult.length === 0 ? this.listBeer : this.searchResult;
//    }
//  }

}
</script>
<style>
@import url('https://fonts.googleapis.com/css?family=Bitter|Josefin+Sans');
@import url('https://fonts.googleapis.com/css?family=Lekton');
.container
{
  /* min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center; */

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
   width: 80%;
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
  /* border: 2px dotted black; */
  display: inline-block;
  vertical-align: middle;
  transform: translateZ(0);
  box-shadow: 0 0 1px rgba(0, 0, 0, 0);
  backface-visibility: hidden;
  -moz-osx-font-smoothing: grayscale;
  transition-duration: 0.3s;
  transition-property: transform;
  transition-timing-function: ease-out;
  transition: 1s;
}
.list {
  height: 100vh;
  overflow-y: auto;

}
</style>
