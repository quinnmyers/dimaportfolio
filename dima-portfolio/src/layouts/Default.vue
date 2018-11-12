<template>
<div v-if='isMounted' ref='wrapper'>
  <app-head></app-head>
   <div class="content">
    <div class="layout">
        <header class="layout__header">
            <!-- <g-link :to="{ name: 'home' }">Gridsome</g-link> -->
          <nav class="layout__header__nav">
            <ul class="layout__header__nav__desktopnav">
              <li class="layout__header__nav__desktopnav__navitem"
                  v-for='(n, index) in navItems'
                  :key='index'
                  ref="navitem">
                  <a :href="buildNavUrl(n.name)" 
                      v-smooth-scroll="{ duration: 1500}"><span class='navitem-text'>{{ n.name }}</span></a>
                  <div :class="`expansion-div-${index} expansion-div`" :ref='`expansiondiv`'></div>
              </li>
            </ul>
            <ul class="layout__header__nav__subnav">
              <li class="layout__header__nav__subnav__subitem"
                  v-for="(s,index) in subNavItems"
                  :key="index"
                  ref="navitem">
                  <span class='navitem-text'>{{ s.name }}</span>
                  <div :class="`expansion-div ${index}`"></div>
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
      lastSectionTargeted: "",
      windowHeight: 0,
      percentArray: [],
      positionArray: [0],
      startEndArray: [],
      totalSectionHeight: 0,
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
    },
    calculatePercents() {
      let testArray = this.layoutSectionArray.map(percent => percent.height);
      this.percentArray = testArray.map(
        percent =>
          (100 * Math.round((10000 * percent) / this.windowHeight)) / 10000
      );
      console.log(`calculate percents: ${this.percentArray}`);
      console.log(`window height: ${this.windowHeight}`);
      console.log(`sectionheights: ${this.totalSectionHeight}`);
      this.sectionStartEnd(this.percentArray);
    },
    sectionStartEnd(array) {
      console.log(array);
      let index = 0;
      let totalElementHeights = 0;
      for (var i = 0; i < array.length; i++) {
        let sectionEndPoint = totalElementHeights + array[i];
        this.startEndArray.push({
          id: i,
          start: totalElementHeights,
          end: sectionEndPoint
        });
        totalElementHeights = sectionEndPoint;
        sectionEndPoint += totalElementHeights;
      }
    },
    determineScrollLocation() {
      const totalHeight = this.totalSectionHeight;
      let scrolledDistance =
        -1 * this.$refs.wrapper.getBoundingClientRect().top;
      let viewportHeight = window.innerHeight;
      let scrollableDistance = totalHeight;
      let percentScrolled = 100 * (scrolledDistance / scrollableDistance);
      this.sectionLocation(percentScrolled);
    },
    ///change where the div is at the end of the function? so that way it starts at 100% on the way back down
    // flex-end at the end, etc
    sectionLocation(p) {
      if (p >= this.startEndArray[0].start && p <= this.startEndArray[0].end) {
        let targetExpansionDiv = this.$refs.expansiondiv[0];
        let currentSectionPercent = this.percentArray[0];
        let differenceOfPercent = 100 / currentSectionPercent;
        let adjustedScrollPosition = p * differenceOfPercent;
        targetExpansionDiv.style.width = `${adjustedScrollPosition}%`;
      } else if (
        p >= this.startEndArray[1].start &&
        p <= this.startEndArray[1].end
      ) {
        let targetExpansionDiv = this.$refs.expansiondiv[1];
        let currentSectionPercent = this.percentArray[1];
        let startingPoint = this.startEndArray[1].start;
        let differenceOfPercent = 100 / currentSectionPercent;
        let adjustedScrollPosition =
          p * differenceOfPercent - startingPoint * differenceOfPercent;
        targetExpansionDiv.style.width = `${adjustedScrollPosition}%`;
      } else if (
        p >= this.startEndArray[2].start &&
        p <= this.startEndArray[2].end
      ) {
        let targetExpansionDiv = this.$refs.expansiondiv[2];
        let currentSectionPercent = this.percentArray[2];
        let startingPoint = this.startEndArray[2].start;
        let differenceOfPercent = 100 / currentSectionPercent;
        let adjustedScrollPosition =
          p * differenceOfPercent - startingPoint * differenceOfPercent;
        targetExpansionDiv.style.width = `${adjustedScrollPosition}%`;
        console.log("you are in the THIRD section");
      } else if (
        p >= this.startEndArray[3].start &&
        p <= this.startEndArray[3].end
      ) {
        let targetExpansionDiv = this.$refs.expansiondiv[3];
        let currentSectionPercent = this.percentArray[3];
        let startingPoint = this.startEndArray[3].start;
        let differenceOfPercent = 100 / currentSectionPercent;
        let adjustedScrollPosition =
          p * differenceOfPercent - startingPoint * differenceOfPercent;
        targetExpansionDiv.style.width = `${adjustedScrollPosition}%`;
        console.log("you are in the FOURTH section");
      } else if (
        p >= this.startEndArray[4].start &&
        p <= this.startEndArray[4].end
      ) {
        let targetExpansionDiv = this.$refs.expansiondiv[4];
        let currentSectionPercent = this.percentArray[4];
        let startingPoint = this.startEndArray[4].start;
        let differenceOfPercent = 100 / currentSectionPercent;
        let adjustedScrollPosition =
          p * differenceOfPercent - startingPoint * differenceOfPercent;
        targetExpansionDiv.style.width = `${adjustedScrollPosition}%`;
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
      this.totalSectionHeight = this.layoutSectionArray
        .map(element => element.height)
        .reduce((a, b) => a + b, 0);
      console.log(`total from reduce: ${this.totalSectionHeight}`);
      this.calculatePercents();
    }
  },
  mounted() {
    this.isMounted = true;
    this.$nextTick(console.log("layout: " + this.layoutSectionArray));
    this.$nextTick(this.measureWindow);
    this.$nextTick(
      window.addEventListener("scroll", this.determineScrollLocation)
      //this.throttle(this.determineScrollLocation, 25)
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
        .navitem-text 
          margin-left: 20px
        &__navitem, &__subitem
          margin: 12px 0px
        .expansion-div
          background: $accent
          height: 2px
          width: 0%
      &__desktopnav
        display: flex 
        flex-direction: column
        margin-top: 20px
        .navitem-text 
          margin-left: 20px
        &__navitem, a, &__:visited, .navitem-text
          display: flex 
          flex-direction: column
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
        display: flex 
        flex-direction: column 
        font-family: $sans-serif
        font-size: 0.9rem 
        color: $grey
        &__subitem 
          display: flex 
          flex-direction: column 
          align-self: flex-start
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
