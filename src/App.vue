<template>
  <div id="app">
    <side-bar-left></side-bar-left>

  </div>
</template>
<script lang="ts">
import sideBarLeft from '../src/components/SideBarLeft.vue'
import { Component, Vue } from 'vue-property-decorator'

@Component({
  components: {
    sideBarLeft
  }
})
export default class App extends Vue {}

</script>
<style lang="scss">
</style>
