<template>
  <div class="page1">
    <h3 class="animated fadeInUp">I am Section 4</h3>
  </div>
</template>

<script>

export default {
  data() {
    return {

    };
  },

  computed: {
    location() {
      return this.$store.state.scormLMS.location
    },
    items() {
      return this.$store.state.items
    }
  },

  methods: {
    checkCue() {
      //BOILERPLATE FOR RUNNING AN INTERVAL
      // var self = this
      // if(Math.floor(self.$refs.audio1.currentTime) == 3){
      //   self.vis1 = "visible"
      // }
    },
    runInterval() {
      //BOILERPLATE FOR RUNNING AN INTERVAL
      this.interval = setInterval(this.checkCue, 100);
    }
  },
  mounted() {

  },
  beforeDestroy() {
    //BOILERPLATE FOR RUNNING AN INTERVAL
    clearInterval(this.interval);
  },
  components: {},
  props: []
};
</script>

<style lang="scss" scoped>

</style>
