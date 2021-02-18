<template>
  <div class="cards">
    <div class="container">
      <nuxt-link
        class="card"
        v-for="film in movies"
        v-if="film.poster_path"
        :key="film.id"
        :to="`/${film.id}`"
      >
        <div class="card-front">
          <img
            :src="`http://image.tmdb.org/t/p/w500/${film.poster_path}`"
            alt="front"
          />
        </div>
        <div class="card-back">
          <h4>{{ film.title }}</h4>
          <p class="date">{{ getYear(film.release_date) }}</p>
          <p v-for="genre in getGenres(film, genres)" :key="genre">
            {{ genre }}
          </p>
          <h2>{{ film.vote_average }} <i class="fas fa-star"></i></h2>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  props: ['movies', 'genres'],
  data() {
    return {};
  },
  methods: {
    getYear(date) {
      return date.slice(0, 4);
    },
    getGenres(film, genresCodes) {
      const ids = film.genre_ids;
      const genres = genresCodes.filter((elem) => {
        if (ids.includes(elem.id)) {
          return elem.name;
        }
      });
      return genres.map((elem) => {
        return elem.name;
      });
    },
  },
};
</script>
