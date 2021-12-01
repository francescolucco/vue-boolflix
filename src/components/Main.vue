<template>
  <div class="box-card-films d-flex justify-content-center flex-wrap">
    <div 
      class="card-film"
      v-for="film in filmsList"
      :key="film.id"
      >
      <h2>Titolo:</h2>
      <h1>{{film.title}}</h1>
      <h2>Titolo originale:</h2>
      <h1>{{film.original_title}}</h1>
      <h2>Lingua:</h2>
      <h1>{{film.original_language}}</h1>
      <h2>Voto:</h2>
      <h1>{{film.vote_average}}</h1>
    </div>
  </div>
</template>

<script>

export default {
   name: "Main",
   props:{
     filmsList: Array
   },
}
</script>

<style lang="scss">
.box-card-films{
  min-height: calc(100vh - 80px);
  .card-film{
    height: 500px;
    width: 200px;
    // background-color: red;
    border: 5px solid rgb(251, 188, 14);
    margin: 30px;
    padding: 20px;
    h1{
      font-size: 20px;
    }
    h2{
      color: rgb(251, 188, 14);
    }
  }
}
</style>

  //  methods:{
  //    getAPI(){
  //      if(this.titleToSend !== 'ww'){
  //        axios.get('https://api.themoviedb.org/3/search/movie',{
  //            params:{
  //              api_key: '27d121d27b7dc4f651e4c2ccb0187202',
  //              query: 'ritorno al futuro',
  //              language: 'it-IT'
  //            }
  //          })
  //        .then(r =>{
  //          console.log(r.data.results);
  //          this.filmsList = r.data.results;
  //        })
  //        .catch(e => {
  //          console.log(e);
  //        })
  //      }
  //    }
  //  },
    // computed:{
    // lanchFunction(){
    //     if(this.titleToSend !== ''){
    //       return this.getAPI();
    //     }
    //   }
    // },
  //  mounted(){
  //    this.getAPI();
  //  }