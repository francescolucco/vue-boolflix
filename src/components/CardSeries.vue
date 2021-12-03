<template>
      <div 
         class="flip-card card-film" 
         v-if="serie.poster_path">
        <div class="flip-card-inner">
          <div class="flip-card-front">
            <img 
            :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`" alt="">
          </div>
          <div class="flip-card-back">
            <h2>Titolo:</h2>
            <h1>{{serie.name}}</h1>
            <h2>Titolo originale:</h2>
            <h1>{{serie.original_name}}</h1>
            <h2>Lingua:</h2>
            <h1>
              <img  v-if="serie.original_language === 'en'" :src="`https://flagcdn.com/224x168/gb-eng.png`" alt="" srcset="">
              <img   v-else-if="serie.original_language !== 'en'" :src="`https://flagcdn.com/224x168/${serie.original_language}.png`" alt="" srcset="">
              <div v-else>flag non trovata</div>
            </h1>
            <h2>Voto:</h2>
            <div
              v-if="serie.vote_average > 0"
              class="box-stars d-flex justify-content-center align-items-center">
              <h1>
  <!-- cliclo con la logica della classe dinamica: molto più compatta e semplice rispetto alla funzione della card movies -->
                <i
                v-for="(star, index) in 5" :key="index" 
                class="fa-star"
                :class="index < Math.round(serie.vote_average/2) ? 'fa-solid' : 'fa-regular'"></i>
              </h1>
            </div>
            <div class="voto-undefaund" v-else>non presente
            </div>
            <div 
               v-if="serie.overview !== ''"
               class="box-trama">
               <h2>Trama:</h2>
               <h1>{{serie.overview}}</h1>
            </div>
          </div>
        </div>
      </div>
</template>

<script>

export default {
  name: 'CardSeries',
  props:{
      serie: Object
  },

}
</script>

<style lang="scss">
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
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  }
  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
      background-color: #000000;

  }
  .flip-card-front, .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
  }
  .flip-card-front {
    background-color: #bbb;
    color: black;
  }
  .flip-card-back {
    background-color: #000000;
    color: white;
    transform: rotateY(180deg);
  }
  .card-film{
    h1{
      font-size: 20px;
    }
    h2{
      color: rgb(251, 188, 14);
    }
    h1 img{
      width: 60%;
      }
  }


</style>