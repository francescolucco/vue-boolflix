<template>
  <div id="carouselExampleControls" class="carousel slide" data-ride="carousel">
    <div class="carousel-inner">
      <div
        class="carousel-item"
        v-for="film in filmsList"
        :key="film.id + 100"
      >
        <div v-if="film.poster_path" class="flip-card card-film">
          <div class="flip-card-inner">
            <div class="flip-card-front">
              <img
                :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`"
                alt=""
              />
            </div>
            <div class="flip-card-back">
              <h2>Titolo:</h2>
              <h1>{{ film.title }}</h1>
              <h2>Titolo originale:</h2>
              <h1>{{ film.original_title }}</h1>
              <h2>Lingua:</h2>
              <h1>
                <img
                  v-if="film.original_language === 'en'"
                  :src="`https://flagcdn.com/224x168/gb-eng.png`"
                  alt=""
                  srcset=""
                />
                <img
                  v-else-if="film.original_language !== 'en'"
                  :src="`https://flagcdn.com/224x168/${film.original_language}.png`"
                  alt=""
                  srcset=""
                />
                <div v-else>flag non trovata</div>
              </h1>
              <div
                class="box-voto d-flex justify-content-center align-items-center"
              >
                <h2>Voto:</h2>
                <div
                  v-if="film.vote_average > 0"
                  class="box-stars d-flex justify-content-center align-items-center"
                >
                  <h1 v-for="(star, index) in film.vote_average" :key="index">
                    <i class="fa-solid fa-star"></i>
                  </h1>
                  <h1
                    v-for="(star, index) in starsVuote(film.vote_average)"
                    :key="index + 10"
                  >
                    <i class="fa-regular fa-star"></i>
                  </h1>
                </div>
                <div class="voto-undefaund" v-else>non presente</div>
              </div>
              <div v-if="film.overview !== ''" class="box-trama">
                <h2>Trama:</h2>
                <h1 class="overview">{{ film.overview }}</h1>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <a
      class="carousel-control-prev"
      href="#carouselExampleControls"
      role="button"
      data-slide="prev"
    >
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="sr-only">Previous</span>
    </a>
    <a
      class="carousel-control-next"
      href="#carouselExampleControls"
      role="button"
      data-slide="next"
    >
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="sr-only">Next</span>
    </a>
  </div>
</template>

<script>
export default {
  name: "Carousel",
  props: {
    filmsList: Object,
  },
  methods: {
    starsVuote(num) {
      let numStarsVuote = parseInt(5 - num);
      return numStarsVuote;
    },
  },
};
</script>

<style lang="scss">
.carousel-inner {
  height: 674px;
  .carousel-inner {
    width: 100%;
    height: 674px;
  }
}
</style>
