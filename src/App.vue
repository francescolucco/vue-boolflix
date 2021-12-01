<template>
  <div>
    <Header @titleSearch="titleToSendApi"/>
    <Main :filmsList="filmsList"/>

  </div>
</template>

<script>
import Header from "./components/Header";
import Main from "./components/Main";
import axios from 'axios';


export default {
  name: 'App',
    data(){
    return{
      titleToSend: '',
      urlTheMovied: 'https://api.themoviedb.org/3/search/movie',
      apiKey: '27d121d27b7dc4f651e4c2ccb0187202',
      languageIt: '&language=it-IT',
      languageEn: '&language=en-US',
      filmsList: []
    }
  },
  components: {
    Header,
    Main,
  },
  methods:{
    titleToSendApi(text){
      this.titleToSend = text;
       if(this.titleToSend !== ''){
         axios.get(this.urlTheMovied,{
             params:{
               api_key: this.apiKey,
               query: this.titleToSend,
               language: 'it-IT'
             }
           })
         .then(r =>{
           console.log(r.data.results);
           this.filmsList = r.data.results;
         })
         .catch(e => {
           console.log(e);
         })
       }
    }
  }
}

</script>

<style lang="scss">
  @import "./assets/styles/general";
</style>
