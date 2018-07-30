<template>
  <div id="app">
    <menuadaptive></menuadaptive>
    <!-- <gallery></gallery> --> 
  </div>
</template>

<script>
import fontawesome from '@fortawesome/fontawesome'
import regular from '@fortawesome/fontawesome-free-regular'
import solid from '@fortawesome/fontawesome-free-solid'
import brands from '@fortawesome/fontawesome-free-brands'

import gallery from './assets/components/gallery/Gallery.vue'
import menuadaptive from './assets/components/menuadaptive/menuadaptive.vue'
export default {
  data () {
    return {
      
    }
  },
  components: {
    gallery,
    menuadaptive
  }
}
</script>

<style lang="scss">

</style>
