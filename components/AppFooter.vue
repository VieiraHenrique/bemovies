<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__block">
        <p><i class="fas fa-film"></i> Be<span>Movies</span></p>
        <small>&copy; 2021. All rights reserved</small>
      </div>
      <div class="footer__block">
        <ul>
          <li>Featured movies</li>
          <SearchBar />
        </ul>
      </div>
      <div class="footer__block">
        <ul>
          <li>Comedy</li>
          <li>Drama</li>
          <li>Romance</li>
          <li>Action</li>
          <li>Thriller</li>
          <li>Horror</li>
        </ul>
      </div>
      <div class="footer__block social">
        <i class="fab fa-facebook"></i>
        <i class="fab fa-instagram-square"></i>
        <i class="fab fa-twitter-square"></i>
        <i class="fab fa-tiktok"></i>
      </div>
    </div>
  </footer>
</template>

<script>
import SearchBar from './SearchBar.vue'
export default {
  components: { SearchBar },
}
</script>
