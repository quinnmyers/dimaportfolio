<template>
<div v-if='isMounted'>
  <app-head></app-head>
   <div class="content">
    <div class="layout">
        <header class="layout__header">
            <!-- <g-link :to="{ name: 'home' }">Gridsome</g-link> -->
          <nav class="layout__header__nav">
            <ul class="layout__header__nav__desktopnav">
              <li class="layout__header__nav__desktopnav__navitem"
                  v-for='(n, index) in navItems'
                  :key='index'>
                  <a :href="buildNavUrl(n.name)" 
                      v-smooth-scroll="{ duration: 1000}">{{ n.name }}</a>
              </li>
            </ul>
            <ul class="layout__header__nav__subnav">
              <li class="layout__header__nav__subnav__subitem"
                  v-for="(s,index) in subNavItems"
                  :key="index">
                  {{ s.name }}
              </li>
            </ul>
            <!-- <g-link class="nav__link" :to="{ name: 'home' }">Home</g-link>
            <g-link class="nav__link" :to="{ name: 'about' }">About</g-link> -->
          </nav>
        </header>
        <div class="pages">
          <slot @testEvent='testFunction'/>
        </div>
      </div>
  </div>
</div>
 
</template>

<script>
import Head from "./Base/Head.vue";

export default {
  props: ["layoutSectionArray"],
  components: {
    appHead: Head
  },
  data() {
    return {
      isMounted: false,
      windowHeight: 0,
      percentArray: [],
      positionArray: [0],
      navItems: [
        {
          name: "Visual Development",
          url: "#visualdevelopment",
          alt: ""
        },
        {
          name: "Illustration",
          url: "#illustration",
          alt: ""
        },
        {
          name: "Sketches",
          url: "#sketches",
          alt: ""
        },
        {
          name: "Social & Mobile",
          url: "#social&mobile",
          alt: ""
        },
        {
          name: "Marketing Posters",
          url: "#",
          alt: ""
        }
      ],
      subNavItems: [
        {
          name: "about",
          url: "#",
          alt: ""
        },
        {
          name: "cv",
          url: "#",
          alt: ""
        },
        {
          name: "contact",
          url: "#",
          alt: ""
        },
        {
          name: "top",
          url: "#",
          alt: ""
        }
      ]
    };
  },
  methods: {
    buildNavUrl(str) {
      const urlPath = `#${str.replace(/\s/g, "").toLowerCase()}`;
      return urlPath;
    },
    measureWindow() {
      this.windowHeight = document.body.clientHeight;
      console.log(this.windowHeight);
    },
    calculatePercents() {
      console.log(this.layoutSectionArray);
      let testArray = this.layoutSectionArray.map(percent => percent.height);
      console.log(testArray);
      this.percentArray = testArray.map(
        percent =>
          (100 * Math.round((10000 * percent) / this.windowHeight)) / 10000
      );
      //THIS IS WHERE I NEED TO FIX THE STARTING POINT %s
      console.log(this.percentArray);
      this.determineScrollLocation();
    },
    determineScrollLocation() {
      var h = document.documentElement,
        b = document.body,
        st = "scrollTop",
        sh = "scrollHeight";
      this.sectionLocation(
        ((h[st] || b[st]) / ((h[sh] || b[sh]) - h.clientHeight)) * 100
      );
    },
    sectionLocation(p) {
      // console.log("HELLO");
      // console.log(p);
      if (p < this.percentArray[0]) {
        console.log("you are in the FIRST section");
      } else if (p > this.percentArray[0] && p < this.percentArray[1]) {
        console.log("you are in the SECOND section");
      } else if (p > this.percentArray[1] && p < this.percentArray[2]) {
        console.log("you are in the THIRD section");
      } else if (p > this.percentArray[2] && p < this.percentArray[3]) {
        console.log("you are in the FOURTH section");
      } else if (p > this.percentArray[4] && p < this.percentArray[5]) {
        console.log("you are in the FIFTH section");
      }
    },
    throttle(fn, wait) {
      let time = Date.now();
      return function() {
        if (time + wait - Date.now() < 0) {
          fn();
          time = Date.now();
        }
      };
    }
  },
  watch: {
    layoutSectionArray: function() {
      this.calculatePercents();
    }
  },
  mounted() {
    this.isMounted = true;
    this.$nextTick(console.log("layout: " + this.layoutSectionArray));
    this.$nextTick(this.measureWindow);
    this.$nextTick(
      window.addEventListener(
        "scroll",
        this.throttle(this.determineScrollLocation, 25)
      )
    );
  }
};
</script>

<style scoped lang="sass">
@import '../base.sass'

.layout
  display: flex
  width: 100%
  &__header 
    display: flex
    flex-direction: column
    background: khaki
    position: sticky 
    top: 0
    width: 225px 
    height: 100vh
    border-left: 5px solid black
    &__nav 
      //main container for nav
      display: flex 
      flex-direction: column
      height: 100%
      //padding and margins for both lists of navitems
      &__desktopnav, &__subnav
        list-style: none 
        &__navitem, &__subitem
          padding-left: 20px
          margin: 12px 0px
      &__desktopnav
        display: flex 
        flex-direction: column
        margin-top: 20px
        &__navitem 
          border-bottom: 1px solid $accent
        &__navitem, a, &__:visited
          display: flex 
          align-self: flex-start
          font-family: $serif
          text-decoration: none
          font-size: 1.1rem
          background: orange
          &:nth-child(1)
            color: blue 
          &:nth-last-child(1)
            color: purple
      &__subnav 
        font-family: $sans-serif
        font-size: 0.9rem 
        color: $grey
        &__subitem 
          background: yellow
          &:nth-child(1)
            color: blue 
          &:nth-last-child(1)
            color: purple
  .pages
    display: flex 
    flex-direction: column 
    flex: 1
    //background: red 
    
</style>
