<template>
  <div>
    <div class="box-card-films d-flex justify-content-center flex-wrap">
      <h1 class="title-section">FILM</h1>
      <CardMovie 
        v-for="film in filmsList"
        :key="film.id"
        :film="film"/>  
    </div>
    <div class="box-serie-films d-flex justify-content-center flex-wrap">
      <h1 class="title-section">serie tv</h1>
      <CardSeries 
        v-for="serie in seriesList"
        :key="serie.id"
        :serie="serie"/>
    </div>
  </div>
</template>

<script>

import CardMovie from "./CardMovie";
import CardSeries from "./CardSeries";

export default {
  name: "Main",
  components: {
    CardMovie,
    CardSeries,
  },
   props:{
     filmsList: Array,
     seriesList: Array,
   },
   
}
</script>

<style lang="scss">
 .title-section{
  font-size: 80px!important;
  font-weight: 700!important;
  text-transform: uppercase;
  text-shadow: 0px 2px 2px black;
  display: block;
  width: 100%;
  padding: 40px 0 40px 300px;
}
</style>

      <!-- <img 
      v-if="availableFlags.includes(film.original_language)" 
      :src="`https://flagcdn.com/24x18/${film.original_language}.png`" 
      alt="" srcset=""> -->
