<template>
<div>
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
                  {{ n.name }}
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
          <slot/>
        </div>
      </div>
  </div>
</div>
 
</template>

<script>
import Head from "./Base/Head.vue";

export default {
  components: {
    appHead: Head
  },
  data() {
    return {
      navItems: [
        {
          name: "Visual Development",
          url: "#",
          alt: ""
        },
        {
          name: "Illustration",
          url: "#",
          alt: ""
        },
        {
          name: "Sketches",
          url: "#",
          alt: ""
        },
        {
          name: "Social & Mobile",
          url: "#",
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
          display: flex 
          align-self: flex-start
          font-family: $serif
          font-size: 1.1rem
          background: orange
          border-bottom: 1px solid $accent
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
    background: red 
    
</style>
