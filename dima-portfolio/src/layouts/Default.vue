<template>
  <div class="layout">
    <header class="header">
      <strong>
        <g-link :to="{ name: 'home' }">Gridsome</g-link>
      </strong>
      <nav class="nav">
        <!-- <g-link class="nav__link" :to="{ name: 'home' }">Home</g-link>
        <g-link class="nav__link" :to="{ name: 'about' }">About</g-link> -->
      </nav>
    </header>
    <slot/>
  </div>
</template>

<style scoped lang="sass">
@import '../base.sass'



</style>
