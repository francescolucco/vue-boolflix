<template>
  <div>
    <Header @titleSearch="titleToSendApi"/>
    <Main :titleToSend="titleToSend"/>

  </div>
</template>

<script>
import Header from "./components/Header";
import Main from "./components/Main";

export default {
  name: 'App',
    data(){
    return{
      titleToSend: ''
    }
  },
  components: {
    Header,
    Main,
  },
  methods:{
    titleToSendApi(text){
      this.titleToSend = text;
    }
  }
}
</script>

<style lang="scss">
  @import "./assets/styles/general";
</style>
