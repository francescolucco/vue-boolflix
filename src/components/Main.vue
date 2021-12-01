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
    background-color: red;
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