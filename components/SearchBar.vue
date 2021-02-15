<template>
  <form @submit.prevent="search" class="SearchBar">
    <input v-model="searchTerm" type="text" placeholder="Search for a movie" />
    <button><i class="fas fa-search"></i></button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      searchTerm: '',
    }
  },
  methods: {
    search: function () {
      this.$emit('searchMovie', this.searchTerm)
      this.searchTerm = ''
    },
  },
}
</script>

<style></style>
