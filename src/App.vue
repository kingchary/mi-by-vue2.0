<template  >
  <div id="app" >
    <top-bar></top-bar>
    <top-header></top-header>
    <top-banner></top-banner>
    <top-sub></top-sub>
    <goods></goods>
    <temp-footer></temp-footer>
    <play-video :play-config="playConfig"></play-video>
    <!-- 这里动态的传递给子子组件 通过:props  -->
  </div>
</template>

<script>
import bus from './components/common/store'
import TopBar from './components/TopBar'
import TopHeader from './components/TopHeader'
import TopBanner from './components/TopBanner'
import TopSub from './components/TopSub'
import Goods from './components/Goods'
import TempFooter from './components/TempFooter'
import PlayVideo from './components/common/PlayVideo'
  console.log(bus)
  export default {
    data () {
      return {
        playConfig: {}
      }
    },
    mounted () {
     this.recivePlayVideo()
    },
    methods: {
      recivePlayVideo (opts) {
        bus.$on('play', (opts) => {
          this.playConfig = opts
        })
      }
    },
    components: {
      'top-bar': TopBar,
      'top-header': TopHeader,
      'top-banner': TopBanner,
      'top-sub': TopSub,
      'goods': Goods,
      'temp-footer': TempFooter,
      'play-video': PlayVideo
    }
  }

</script>
<style>
  @import './assets/css/base.css';
</style>
