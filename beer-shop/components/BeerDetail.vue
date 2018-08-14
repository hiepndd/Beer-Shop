<template>
  <div class="ml-10">
           <h1>  {{ id }} </h1>
   </div>
</template>
<script>
import axios from 'axios'
export default {
 props: ["id"],
 data (){
   beer: []
 },
 async asyncData({ params, error }) {
      try {
        const {data} = await axios.get(`https://api.punkapi.com/v2/beers/${id}`)
        return {
          beer: data[0]
        }
      } catch (e) {
        error({ message: 'User not found', statusCode: 404 })
      }
    },

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
