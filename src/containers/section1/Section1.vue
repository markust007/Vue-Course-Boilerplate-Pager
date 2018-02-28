<template>
  <section id="section1">

    <page1 v-show="location === 1"></page1>
    <page2 v-show="location === 2"></page2>


  </section>
</template>

<script>
import page1 from './pages/Page1.vue'
import page2 from './pages/Page2.vue'

  export default {
    data: function () {
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
      page1, page2
    },
    props: []
  }
</script>

<style scoped>

</style>
