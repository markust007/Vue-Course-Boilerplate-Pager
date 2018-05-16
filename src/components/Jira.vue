<template>
    <button class="jira" @click="launchCollector">Feedback</button>
</template>

<script>
  export default {
    data() {
      return {

        }
      },
      computed: {
        userLocation () {
          return this.$store.state.userLocation
        }
      },
      methods: {
        launchCollector() {
          const location = this.userLocation.replace('#', '%23');
          // I like to use the location as the default summary
          // This is optional - you don't have to pass in a summary value at all
          const summary = location;
          const collectorURL = 'collector.html' + '?location=' + location + '&summary=' + summary;
          const windowName = "_blank";
          const windowSpecs = "height=727px, width=820px, location=0, menubar=0, scrollbars=0, status=0, titlebar=0, toolbar=0";
          window.open(collectorURL, windowName, windowSpecs);
        }
      }
    }
</script>

<style lang="scss" scoped>
.jira {
  position: fixed;
  bottom: auto;
  left: 0;
  top: 10px;
  color: #fff;
  z-index: 999;
  background-color: #000;
  padding: .4rem .75rem;
  border: 0px;
  border-bottom-right-radius: 8px;
  border-top-right-radius: 8px;
  font-size: 1rem;
  border-bottom: 0px solid #666;
}
</style>
