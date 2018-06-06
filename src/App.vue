<template>
  <div id="app" v-if="items && config">
    <!-- JIRA - REMOVE FOR GOLD -->
    <Jira v-if="config.jira"></Jira>
    <Jira-position v-if="config.jira"></Jira-position>

    <!-- LOADING ICON -->
    <transition name="fade">
      <i class="fa fa-circle-o-notch fa-spin fa-3x fa-fw" v-show="loader"></i>
    </transition>


    <!-- MAIN -->
    <Top :items="items"></Top>
    <Resources :items="items" v-show="menu"></Resources>
    <keep-alive>
      <component :is="theLocation"></component>
    </keep-alive>
    <!-- <Section1 v-show="location <= 2"></Section1>
    <Section2 v-show="location > 2"></Section2> -->
    <Bottom :items="items"></Bottom>
    <Navigation></Navigation>

  </div>
</template>

<script>
/////////////////////IMPORTS/////////////////////////
/////////////////////////////////////////////////////
import store from './store/index'
import Jira from './components/Jira.vue'
import JiraPosition from './components/JiraPosition.vue'
import Top from './components/Top.vue'
import Bottom from './components/Bottom.vue'
import Navigation from './components/Navigation.vue'
import Resources from './components/Resources.vue'
import Section1 from './containers/Section1/Container.vue'
import Section2 from './containers/Section2/Container.vue'
import Section3 from './containers/Section3/Container.vue'
import Section4 from './containers/Section4/Container.vue'

import {polyfill} from "mobile-drag-drop";
import {scrollBehaviourDragImageTranslateOverride} from "mobile-drag-drop/scroll-behaviour";
/////////////////////VARIABLES & MISC/////////////////////
/////////////////////////////////////////////////////////
polyfill({
    // use this to make use of the scroll behaviour
    dragImageTranslateOverride: scrollBehaviourDragImageTranslateOverride
});

export default {
  name: 'app',
  store,
  data () {
    return {
      loader: true
    }
  },
  computed: {
    location () {
      return this.$store.state.scormLMS.location
    },
    menu () {
      return this.$store.state.menu.menu
    },
    items() {
      return this.$store.state.items
    },
    config() {
      return this.$store.state.config
    },
    theLocation() {
      let match
      const finalArray = []
      // const getObjectStart = (obj) => obj.first
      // finalArray = this.config.sections.map(getObjectStart)
      this.config.sections.map((value, index) => {
        finalArray.push(value.first)
      })
      // console.log(finalArray)
      let number = finalArray.find(k => k > this.location);
      // console.log(number)
      if(this.location == 1) {
        match = 1
      } else if(!number) {
        match = finalArray.length;
      } else {
        match = finalArray.findIndex(k => k === number);
      }
      // console.log(match)
      const theValue = "Section" + match + ""
      // console.log(theValue)
      return theValue
    }
  },
  methods: {
    menuToggle () {
      this.$store.commit('menu/menuToggle')
    }
  },
  mounted() {
    this.loader = false;
    if(this.config) {

    }
    //scorm
    this.$store.commit('scormLMS/scormInit');
  },
  components: {
    Jira, JiraPosition, Top, Bottom, Navigation, Resources, Section1, Section2, Section3, Section4
  }
}
</script>

<!-- REMOVE 'SCOPED' FOR GLOBAL STYLES -->
<style lang="scss">
</style>
