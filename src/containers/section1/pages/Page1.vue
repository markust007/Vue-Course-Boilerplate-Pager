<template>
  <div class="page1 animated fadeIn">
    <div class="container">
      <h3 class="title animated fadeInUp">{{items.s1page1[0].title}}</h3>
      <p v-html="items.s1page1[0].text" class="animated fadeInUp"></p>
    </div>
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
    setTimeout(() => {

    }, 50);

  },
  beforeDestroy() {
    //BOILERPLATE FOR RUNNING AN INTERVAL
    clearInterval(this.interval);
  },
  components: {},
  props: []
};
</script>

<style scoped>

</style>
