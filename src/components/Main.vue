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
       <h1 v-if="lenguages">
        {{film.original_language}}
        </h1>
        <div
          class="box-img"
          v-if="EnLenguage">
          <img  src="../assets/img/united_kingdom_flags_flag_17079.png" alt="">
        </div>
        <div
          class="box-img"
          v-if="itLenguage">
          <img  src="../assets/img/italy_flags_flag_17018.png" alt="">
        </div>
      <h2>Voto:</h2>
      <h1>{{film.vote_average}}</h1>
    </div>
  </div>
</template>

<script>

export default {
   name: "Main",
   data(){
     return{
       lenguages: false,
       enLenguage: false,
       itLenguages: false,
     }
   },
   props:{
     filmsList: Array,
     lenguageList: Array
   },
   methods:{
    //  stampFlag(){
    //    this.lenguageList.forEach(lenguage=>{
    //      if(lenguage === 'en'){
    //        this.enLenguage = true
    //      }else if(lenguage === 'it'){
    //        this.itLenguages = true
    //      }else{
    //        this.lenguages = true
    //      }
    //    })
    //  }
  },
  computed:{
         stampFlag(){
       this.lenguageList.forEach(lenguage=>{
         if(lenguage === 'en'){
           this.enLenguage = true
           return this.enLenguage
         }else if(lenguage === 'it'){
           this.itLenguages = true
           return this.itLenguage
         }else{
           this.lenguages = true
           return this.lenguage
         }
       })
     }
  }
   
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
    .box-img{
      width: 100%;
      text-align: center;
      img{
        width: 25%;
      }

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