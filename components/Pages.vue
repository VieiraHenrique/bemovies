<template>
  <div class="pages">
    <i class="fas fa-chevron-left" @click="prev()"></i>
    <p>{{ page }}</p>
    <i class="fas fa-chevron-right" @click="next()"></i>
  </div>
</template>

<script>
export default {
  props: ['page'],
  data() {
    return {}
  },
  methods: {
    prev() {
      this.$emit('prev')
    },
    next() {
      this.$emit('next')
    },
  },
}
</script>

<style></style>
