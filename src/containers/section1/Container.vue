<template>
  <section id="section1">

    <Page1 v-show="location === 1"></Page1>
    <Page2 v-show="location === 2"></Page2>


  </section>
</template>

<script>
import Page1 from './pages/Page1.vue'
import Page2 from './pages/Page2.vue'

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
      Page1, Page2
    },
    props: []
  }
</script>

<style lang="scss" scoped>

</style>
