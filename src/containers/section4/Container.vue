<template>
  <section id="section4">

    <p>
      Section4
    </p>
    <keep-alive>
      <component :is="comp"></component>
    </keep-alive>

  </section>
</template>

<script>
import Page1 from './pages/Page1.vue'
import Page2 from './pages/Page1.vue'
import Page3 from './pages/Page1.vue'

  export default {
    data() {
      return {
        index: 3
      }
    },
    computed: {
      location () {
        return this.$store.state.scormLMS.location
      },
      config() {
        return this.$store.state.config
      },
      comp() {
        let array = []

        for(let i = 0; i < this.config.sections[this.index].pages; i++) {
          const first = this.config.sections[this.index].first
          array.push(first + i);
        }
        // console.log(this.config.sections[this.index].pages)
        // console.log(this.config.sections[this.index].first)
        // console.log(array)
        const page = array.findIndex(k => k === this.location) + 1;
        let final = "Page" + page + ""
        // console.log(final)
        return final
      }
    },
    methods: {

    },
    mounted() {

    },
    components: {
      Page1, Page2, Page3
    },
    props: []
  }
</script>

<style lang="scss" scoped>

</style>
