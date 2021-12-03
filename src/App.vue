<template>
  <div>
    <Header @titleSearch="titleToSendApi" 
    @returnHome="this.getApipopular('movie')"/>
    <Main :filmsList="movie" :seriesList="tv" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Main from "./components/Main";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      titleToSend: "dante",
      urlAPI: "https://api.themoviedb.org/3/search/",
      apiKey: "27d121d27b7dc4f651e4c2ccb0187202",
      movie: [],
      tv: [],

      urlSeriesTv: "https://api.themoviedb.org/3/search/tv",
    };
  },
  components: {
    Header,
    Main,
  },
  methods: {
    titleToSendApi(text) {
      this.titleToSend = text;
      if (this.titleToSend !== "") {
        this.getApi('movie');
        this.getApi('tv');
      }
    },
// Faccio chiamata unica al serve API: per farlo devo passare una variabile type che può assumere più valori (in questo caso movie e tv). Quando poi richiamo i dati con this[type] utilizzo una proprietà degli oggetti per la quale mi restituisce con una solo chiamata (ad es. una console log) tutti i valori, stringa array oggetti ecc che type può aver assunto. In questo caso this[type] si riferisce a this.movie e a this.tv che sono due array distinti.
    getApi(type) {
      axios
        .get(this.urlAPI+type, {
          params: {
            api_key: this.apiKey,
            query: this.titleToSend,
            language: "it-IT",
          },
        })
        .then((r) => {
          this[type] = r.data.results;
          this[type].forEach((film) => {
            let numStars = Math.round((parseInt(film.vote_average) * 5) / 10);
            film.vote_average = numStars;
          });
          console.log(this[type]);
        })
        .catch((e) => {
          console.log(e);
        });
    },
//  ho creato una chiamta API per gestire il caricamento dei film e delle serie pi+ popolari. Gestisco le due chiamate con la stessa funzione. utilizzo gli stessi array delle chiamta API delle ricerche, in  modo che alla ricerca gli array vengano svuotati e ripopolati
        getApipopular(type) {
      axios
        .get('https://api.themoviedb.org/3/'+type+'/popular?api_key=27d121d27b7dc4f651e4c2ccb0187202')
        .then((r) => {
          this[type] = r.data.results;
          this[type].forEach((film) => {
            let numStars = Math.round((parseInt(film.vote_average) * 5) / 10);
            film.vote_average = numStars;
          });
          console.log(this[type]);
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
    mounted() {

      this.getApipopular('movie');
      this.getApipopular('tv');
    },

};
</script>

<style lang="scss">
@import "./assets/styles/general";
</style>

