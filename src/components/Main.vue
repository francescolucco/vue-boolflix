<template>
  <div>
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
        <!-- LINGUA -->
        <h2>Lingua:</h2>

        <h1>
          <img  v-if="film.original_language === 'en'" :src="`https://flagcdn.com/24x18/gb-eng.png`" alt="" srcset="">
          <img   v-else-if="film.original_language === 'cs'" :src="`https://flagcdn.com/24x18/cz.png`" alt="" srcset="">
          <img   v-else-if="film.original_language !== 'en'" :src="`https://flagcdn.com/24x18/${film.original_language}.png`" alt="" srcset="">
          <!-- <img v-if="availableFlags.includes(film.original_language)" :src="`https://flagcdn.com/24x18/${film.original_language}.png`" alt="" srcset=""> -->
          <!-- <img v-if="this.lenguageList.includes(film.original_language)" :src="require(`../assets/img/${film.original_language}.png`)" alt="" srcset=""> -->
          <div v-else>flag non trovata</div>
          </h1>
        <h2>Voto:</h2>
        <h1>{{film.vote_average}}</h1>
      </div>
    </div>

    
    <div class="box-serie-films d-flex justify-content-center flex-wrap">
      <div 
        class="card-film"
        v-for="serie in seriesList"
        :key="serie.id"
        >
        <h2>Titolo:</h2>
        <h1>{{serie.name}}</h1>
        <h2>Titolo originale:</h2>
        <h1>{{serie.original_name}}</h1>
        <!-- LINGUA -->
        <h2>Lingua:</h2>
        <h1>
          <img  v-if="serie.original_language === 'en'" :src="`https://flagcdn.com/24x18/gb-eng.png`" alt="" srcset="">
          <img   v-else-if="serie.original_language === 'cs'" :src="`https://flagcdn.com/24x18/cz.png`" alt="" srcset="">
          <img   v-else-if="serie.original_language !== 'en'" :src="`https://flagcdn.com/24x18/${serie.original_language}.png`" alt="" srcset="">
          <!-- <img v-if="availableFlags.includes(film.original_language)" :src="`https://flagcdn.com/24x18/${film.original_language}.png`" alt="" srcset=""> -->
          <!-- <img v-if="this.lenguageList.includes(film.original_language)" :src="require(`../assets/img/${film.original_language}.png`)" alt="" srcset=""> -->
          <div v-else>flag non trovata</div>
          </h1>
        <h2>Voto:</h2>
        <h1>{{serie.vote_average}}</h1>
      </div>
    </div>
  </div>
</template>

<script>

export default {
   name: "Main",
   data(){
     return{
      //  availableFlags : ['it', 'en']
     }
   },
   props:{
     filmsList: Array,
     seriesList: Array,
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
    h1 img{
        width: 25%;
      }
  }
}
.box-serie-films{
  min-height: calc(100vh - 80px);
  .card-film{
    height: 500px;
    width: 200px;
    // background-color: red;
    border: 5px solid rgb(14, 251, 26);
    margin: 30px;
    padding: 20px;
    h1{
      font-size: 20px;
    }
    h2{
      color: rgb(251, 188, 14);
    }
    h1 img{
        width: 25%;
      }
  }
}
</style>
