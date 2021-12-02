<template>
  <div>
    <Header @titleSearch="titleToSendApi"/>
    <Main 
    :filmsList="filmsList"
    :seriesList="seriesList"/>

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
      titleToSend: 'dante',
      urlTheMovied: 'https://api.themoviedb.org/3/search/movie',
      apiKey: '27d121d27b7dc4f651e4c2ccb0187202',
      filmsList: [],

      urlSeriesTv: 'https://api.themoviedb.org/3/search/tv',
      seriesList: [],
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
         this.getApimovie();
         this.getApiseries();
       }
    },

    getApimovie(){
      //  chiamata FILM ********************§§§§§
         axios.get(this.urlTheMovied,{
           params:{
             api_key: this.apiKey,
               query: this.titleToSend,
               language: 'it-IT',
             }
           })
         .then(r =>{
          //  console.log(r.data.results);
           this.filmsList = r.data.results;
           this.filmsList.forEach(stars=>{
            let numStars = Math.round((parseInt(stars.vote_average)*5)/10);
            stars.vote_average = [];
            for(let i = 0; i < numStars; i++){
              stars.vote_average.push(i)
            }
           })
           console.log(this.filmsList);
         })
         .catch(e => {
           console.log(e);
         })
        //  ********************************§§§§§§§
    },

    getApiseries(){
      //  chiamata SERIE TV **************§§§§§§§
      axios.get(this.urlSeriesTv,{
        params:{
          api_key: this.apiKey,
            query: this.titleToSend,
            language: 'it-IT',
          }
        })
      .then(r =>{
        this.seriesList = r.data.results;
        this.seriesList.forEach(stars=>{
          let numStars = Math.round((parseInt(stars.vote_average)*5)/10);
          stars.vote_average = [];
          for(let i = 0; i < numStars; i++){
            stars.vote_average.push(i)
          }
        })
        console.log(this.seriesList);
      })
      .catch(e => {
        console.log(e);
      })
    },
      //  ********************************§§§§§§§

  },
  mounted(){
    this.getApimovie();
    this.getApiseries();
  }
}
</script>

<style lang="scss">
  @import "./assets/styles/general";
</style>
