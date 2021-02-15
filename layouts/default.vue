<template>
  <div>
    <AppHeader />
    <Nuxt />
    <AppFooter />
  </div>
</template>

<script>
import AppHeader from '~/components/AppHeader'
import AppFooter from '~/components/AppFooter'

export default {
  components: { AppHeader, AppFooter },
}
</script>

<style lang="scss">
@import '~/assets/sass/styles.scss';
</style>
