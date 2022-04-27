<script>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup


import axios from 'axios';

export default {  
    data: () => ({
    json: [],
  }),

 methods:{
     async preload() {
        try {
          const response = await axios.get('https://api.spotify.com/v1/artists/6RYrVybxw2eMM5xXCibQF3/top-tracks?market=FR',{
              headers: {
                    Accept: 'application/json',
                    Authorization: "",
                    'Content-Type': 'application/json',
                },
          })
          this.json=response.data
          console.log(this.json)
        this.size = this.json.length
        } catch(err) {

        console.log("err", err)
        }
     },
 },
 mounted(){

  this.preload()
 }
}
</script>

<template>

<p>hey</p>

<div v-for="item in json.tracks" :key="item.name">
 <p>{{item.name}}</p>
    <img :src= item.album.images[1].url>
</div>

</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}
.card-img-top{
  max-height: 230px;
}

</style>
