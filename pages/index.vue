<template>
  <div class="home">
    <Banner />
    <Pages v-if="showPagination" :page="page" @prev="prev()" @next="next()" />
    <Cards :movies="movies" :genres="genres" />
    <Pages v-if="showPagination" :page="page" @prev="prev()" @next="next()" />
  </div>
</template>

<script>
import axios from 'axios';
import Banner from '~/components/Banner';
import Cards from '~/components/Cards';
import Pages from '~/components/Pages';

export default {
  components: { Banner, Cards, Pages },
  data() {
    return {
      page: 1,
      movies: [],
      genres: [],
      showPagination: true,
    };
  },
  methods: {
    prev() {
      if (this.page > 1) {
        this.page--;
      }
    },
    next() {
      if (this.page < 9) {
        this.page++;
      }
    },
    fetchFeatured: async function () {
      const m = await axios.get(
        `https://api.themoviedb.org/3/discover/movie?api_key=112ca2b68890cedc6cd02c2b81593072&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=${this.page}`
      );
      const g = await axios.get(
        'https://api.themoviedb.org/3/genre/movie/list?api_key=112ca2b68890cedc6cd02c2b81593072&language=en-US'
      );
      this.movies = [...m.data.results];
      this.genres = [...g.data.genres];
    },
    fetchSearch: async function (searchTerm) {
      const m = await axios.get(
        `https://api.themoviedb.org/3/search/movie?api_key=112ca2b68890cedc6cd02c2b81593072&language=en-US&query=${searchTerm}&page=${this.page}&include_adult=false`
      );
      this.movies = [...m.data.results];
    },
  },
  watch: {
    page() {
      this.fetchFeatured();
    },
  },
  created() {
    this.fetchFeatured();
    this.$nuxt.$on('featured', () => {
      this.page = 1;
      this.showPagination = true;
      this.fetchFeatured();
    });
    this.$nuxt.$on('searchMovie', (searchTerm) => {
      this.page = 1;
      this.showPagination = false;
      this.fetchSearch(searchTerm);
    });
  },
};
</script>
