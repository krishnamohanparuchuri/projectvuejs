<template>
  <div class="home">
    <h1>oplask</h1>
    
    <input type="text" v-model="inputText" v-on:keyup.enter="searchPhotos" placeholder="type something...">
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';

export default {
  name: 'Home',
  data(){
    return{
       inputText:'',
       images:[]
    }
  },
  methods:{
    searchPhotos(){

      const baseUrl = 'https://api.unsplash.com/search/photos'
      const id= '7H3IZwB8n0-a_9BB1MAviLO2R2w9m8aC6SojsUb8jQc'
      // const id1 ='Z61F6fh5_ihP7cx28_0akGyV3BHLInT8VKi4i7Dw88Q'
      const page='1'
      // const per_page='9'


      axios.get(`${baseUrl}?client_id=${id}/?page=${page}&query=${this.inputText}`)
       .then(res => this.images= res.data)
       console.log(this.images)

    }
  }
}
</script>

<style>
h1{
  font-size:48px;
  display:flex;
  flex-direction: column;
}
input{
  width:80%;
  border-radius:15px;
  height:50px;
  background-color:light grey;
  font-size:28px;

}
</style>
