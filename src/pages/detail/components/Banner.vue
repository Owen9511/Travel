<template>
  <div>
    <div
      class="banner"
      @click="handleBannerClick">
      <img
        class="banner-img"
        src="//img1.qunarzz.com/sight/p0/1412/77/cb5a5c0c47e96f6b42ce646cddf4af0d.water.jpg_600x330_17d4b9aa.jpg"/>
      <div class="banner-info">
        <div class="banner-title">鸟巢(AAAAA景区)</div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe6f5;</span>
          138
        </div>
      </div>
    </div>
    <common-gallery
      :imgs="imgs"
      v-show="showGallary"
      @close="closeGallary"/>
  </div>
</template>

<script>
import CommonGallery from 'common/gallary/Gallary'
export default {
  name: 'Detail',
  components: {
    CommonGallery
  },
  data () {
    return {
      showGallary: false,
      imgs: ['http://img1.qunarzz.com/sight/p0/1412/f7/73c43024f19e33c695b364ccea1db63b.water.jpg_r_800x800_9cc7ad8b.jpg',
        'http://img1.qunarzz.com/sight/p0/1507/c9/eefaa23facb37ac4814e336070207804.water.jpg_r_800x800_c58340e6.jpg']
    }
  },
  activated () {
    this.showGallary = false
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    closeGallary () {
      this.showGallary = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position: relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-info
      display: flex
      position: absolute
      left: 0
      right: 0
      bottom: 0
      line-height: .6rem
      color: #fff
      background-image: linear-gradient(top, rgba(0,0,0,0), rgba(0,0,0,0.8))
      .banner-title
        font-size: .32rem
        padding: 0 .2rem
        flex: 1
      .banner-number
        margin-top: .14rem
        padding: 0 .4rem
        height: .32rem
        line-height: .32rem
        border-radius: .2rem
        background: rgba(0,0,0,.8)
        font-size: .24rem
        .banner-icon
          font-size: .24rem
</style>
