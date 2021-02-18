<template>
  <div class="singleMovie">
    <div class="container">
      <div class="singleMovie__left">
        <h2>{{ movie.title }}</h2>
        <h3>{{ year }}</h3>
        <p>{{ movie.overview }}</p>
      </div>
      <div class="singleMovie__right">
        <iframe
          width="100%"
          height="315"
          :src="`https://www.youtube.com/embed/${video}`"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
        ></iframe>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      movie: {},
      year: null,
      video: null,
    };
  },
  methods: {
    fetchMovie: async function () {
      const m = await axios.get(
        `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=112ca2b68890cedc6cd02c2b81593072&language=en-US`
      );
      const v = await axios.get(`
https://api.themoviedb.org/3/movie/${this.$route.params.id}/videos?api_key=112ca2b68890cedc6cd02c2b81593072&language=en-US`);
      console.log(m.data);
      this.movie = { ...m.data };
      this.year = this.movie.release_date.slice(0, 4);
      console.log(v.data.results);
      this.video = v.data.results[0].key;
    },
  },
  created() {
    this.fetchMovie();
  },
};
</script>

<style></style>
