<template>
  <div>
    <detail-banner
      :sightName="sightName"
      :bannerImg="bannerImg"
      :gallaryImgs="gallaryImgs"/>
    <detail-header/>
    <div class="content">
      <detail-list :list="list"/>
    </div>
  </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  mounted () {
    this.getDetailInfo()
  },
  activated () {
    if (this.lastId && this.$route.params.id !== this.lastId) {
      this.getDetailInfo()
    }
  },
  data () {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      list: [],
      bannerInfo: {},
      lastId: ''
    }
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.handleGetDataSucc)
    },
    handleGetDataSucc (res) {
      this.lastId = this.$route.params.id
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.list = data.categoryList
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .content
    height: 100rem
</style>
