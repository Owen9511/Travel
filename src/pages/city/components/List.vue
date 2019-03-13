<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div
            class="button-wrapper"
            v-for="hotCity of hotCities"
            :key="hotCity.id"
            @click="handleCityClick(hotCity.name)">
            <div class="button">{{hotCity.name}}</div>
          </div>
        </div>
      </div>
      <div
        class="area"
        v-for="(alphabetCities,alphabet) of cities"
        :key="alphabet"
        :ref="alphabet">
        <div class="title border-topbottom">{{alphabet}}</div>
        <div class="item-list">
          <div
            class="item border-bottom"
            v-for="city of alphabetCities"
            :key="city.id"
            @click="handleCityClick(city.name)">
            {{city.name}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import {mapState, mapMutations} from 'vuex'
export default {
  name: 'CityList',
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper, {})
  },
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  computed: {
    ...mapState(['city'])
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/variables.styl'
    .boder-topbottom
      &:before
        border-color: #ccc
      &:after
        border-color: #ccc
    .border-bottom
      &:before
        border-color: #ccc
    .list
      overflow: hidden
      position: absolute
      top: 1.58rem
      left: 0
      right: 0
      bottom: 0
      .title
        line-height: .54rem
        background: #eee
        padding-left: .2rem
        color: #666
        font-size: .26rem
      .button-list
        overflow: hidden
        padding: .1rem .6rem .1rem .1rem
        .button-wrapper
          width: 33.33%
          float: left
          .button
            text-align: center
            margin: .1rem
            padding: .1rem 0
            border: .02rem solid #ccc
            border-radius: .06rem
      .item-list
        .item
          line-height: .64rem
          padding-left: .2rem
</style>
