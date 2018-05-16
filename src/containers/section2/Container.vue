<template>
  <section id="section2">

    <Page1 v-show="location === 3"></Page1>

  </section>
</template>

<script>
import Page1 from './pages/Page1.vue'

  export default {
    data() {
      return {

      }
    },
    computed: {
      location () {
        return this.$store.state.scormLMS.location
      }
    },
    methods: {

    },
    mounted() {

    },
    components: {
      Page1
    },
    props: []
  }
</script>

<style lang="scss" scoped>

</style>
