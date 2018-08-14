<template>
  <div class="container mx-auto max-w-full">
   <div class="flex">
    <div class="container w-1/3 list" >


    </div>
    <div class="container mx-auto w-2/3 mt-1 listdetail">
           <div class="flex flex-wrap mt-32 ">
            <div class="w-1/3 -mt-20 -ml-20 ">
                 <img :src="beer.image_url" alt="">
                 <!-- <h1> {{ beer.image_url}}</h1> -->
            </div>
            <div class="w-2/3 block">
                <h3>{{ beer.name }}</h3>
                <h1 class="text-base mt-10">{{ beer.description }}</h1>

            </div>

           </div>
    </div>
   </div>
  </div>
</template>

<script>
import axios from 'axios'
// import BeerDetail from '~/components/BeerDetail.vue'

  export default {
 data() {
   return {
     id: this.$route.params.id,
     beer: [],
   }
 },
 created(){
    axios.get(`https://api.punkapi.com/v2/beers/${this.id}`)
    .then (response =>{
      this.beer = response.data[0]
    })
  },



  }
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Bitter|Josefin+Sans');
@import url('https://fonts.googleapis.com/css?family=Lekton');
img {
  height: 500px;
  width: auto;
  margin: 0 auto;
  display:block;
}
h4{
   font-family: 'Lekton', sans-serif;
}
h1, h3 {
   font-family: 'Lekton', sans-serif;
}
</style>
