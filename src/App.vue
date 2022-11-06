<template>
  <div id=HG>
      <header><div @click="toggleNav()">☰</div></header>
      <nav>
          <router-link to="/">Home</router-link><br>
          <router-link to="/about">About</router-link><br>
      </nav>
      <router-view/>
      <aside>ASIDE</aside>
      <footer>{{ shrink }}</footer>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup() {
      const shrink = ref( false )
      return {
          shrink
      ,   toggleNav   : () => {
              document.querySelector( 'nav' ).style.width = shrink.value ? '200px' : '100px'
              shrink.value = !shrink.value
          }
      }
  }
}
</script>

<style>
#HG {
;   height                  : 100%
;   display                 : grid
;   grid-template-rows      : 32px 1fr 32px
;   grid-template-columns   : auto 1fr auto
}
nav, aside {
;   width                   : 200px
;   background              : lightgreen
;   transition              : all 300ms 0s ease
}
header, footer {
;   grid-column             : 1 / 4
;   background              : pink
}
</style>