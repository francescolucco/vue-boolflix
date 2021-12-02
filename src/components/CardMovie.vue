<template>
      <div 
         v-if="film.poster_path"
         class="flip-card card-film">
        <div class="flip-card-inner">
          <div class="flip-card-front">
            <img :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`" alt="">
          </div>
          <div class="flip-card-back">
            <h2>Titolo:</h2>
            <h1>{{film.title}}</h1>
            <h2>Titolo originale:</h2>
            <h1>{{film.original_title}}</h1>
            <h2>Lingua:</h2>
            <h1>
              <img  v-if="film.original_language === 'en'" :src="`https://flagcdn.com/224x168/gb-eng.png`" alt="" srcset="">
              <img   v-else-if="film.original_language !== 'en'" :src="`https://flagcdn.com/224x168/${film.original_language}.png`" alt="" srcset="">
              <div v-else>flag non trovata</div>
            </h1>
            <div class="box-voto d-flex justify-content-center align-items-center">
               <h2>Voto:</h2>
               <div
                  v-if="film.vote_average[0] !== ''" 
                  class="box-stars d-flex justify-content-center align-items-center">
                  <h1
                  v-for="(star, index) in film.vote_average"
                  :key="index">
                     <i class="fa-solid fa-star"></i>
                  </h1>
               </div>
               <div
                  class="voto-undefaund" 
                  v-else>non presente
               </div>
               <h1>{{film.vote_average}}</h1>
            </div>
          </div>
        </div>
      </div>
</template>

<script>

   export default {
      name: 'CardMovie',
      props:{
         film: Object
      },
      
}
</script>

<style lang="scss" scope>
  .flip-card {
    background-color: transparent;
    width: 450px;
    height: 674px;
    perspective: 3000px;
  }
  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.561);
  }
  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }
  .flip-card-front, .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
  }
  .flip-card-front {
    background-color: rgb(0, 0, 0);
    color: black;
    overflow: hidden;
   //  object-fit: cover;
    img{
       object-fit: cover;
       width: 100%;
       height: 100%;
       
    }
  }
  .flip-card-back {
    background-color: #000000;
    color: white;
    transform: rotateY(180deg);
  }
  .card-film{
    h1{
      font-size: 20px!important;
    }
    h2{
      color: rgb(251, 188, 14);
    }
    h1 img{
      width: 60%;
      }
    i{
      margin-left: 5px;
      color: yellow!important;
      }
   .voto-undefaund{
      color: white;
   }
  }

</style>