<template>
  <header class="header">
    <div class="container">
      <div class="header__logo">
        <h1><i class="fas fa-film"></i> Be<span>Movies</span></h1>
      </div>
      <div class="header__menu">
        <i @click="toggleMenu" class="fas fa-bars"></i>
        <ul class="header__menu--main" :class="drawer ? 'open' : ''">
          <form>
            <input type="text" placeholder="Search for a movie" />
            <button><i class="fas fa-search"></i></button>
          </form>
          <li>Featured Movies</li>
          <li class="login">Login</li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
    }
  },
  methods: {
    toggleMenu: function () {
      this.drawer = !this.drawer
    },
  },
}
</script>
