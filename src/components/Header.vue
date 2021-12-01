<template>
  <header class="d-flex justify-content-around align-items-center">
    <img src="../assets/logo.png" alt="">
    <div class="search">
      <input 
        type="text" 
        placeholder="Inserisci un titolo"
        v-model= "textSearch">
      <button 
        class="btn btn-success"
        @click="$emit('titleSearch', textSearch)">
        Cerca
      </button>
    </div>
  </header>
</template>

<script>
export default {
   name: "Header",
   data(){
     return{
       textSearch: ''
     }
   }
}
</script>

<style lang="scss">
header{
  height: 80px;
  background-color: rgb(4, 50, 110);
  img{
    height: 100%;
  }
  .search{
    input{
      margin-right: 15px;
    }
  }
}

</style>