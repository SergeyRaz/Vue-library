<template>
  <div id="app">
    <!-- <menuadaptive></menuadaptive> --> <!--Адаптивное меню-->
    <!-- <gallery></gallery> --> <!--Слайдер галерея картинок и т.д.-->
    <popup></popup> <!--Выпадающее окно-->
  </div>
</template>

<script>
import fontawesome from '@fortawesome/fontawesome'
import regular from '@fortawesome/fontawesome-free-regular'
import solid from '@fortawesome/fontawesome-free-solid'
import brands from '@fortawesome/fontawesome-free-brands'

import gallery from './assets/components/gallery/Gallery.vue'
import menuadaptive from './assets/components/menuadaptive/menuadaptive.vue'
import popup from './assets/components/popup/popup.vue'
export default {
  data () {
    return {
      
    }
  },
  components: {
    gallery,
    menuadaptive,
    popup
  }
}
</script>

<style lang="scss">

</style>
