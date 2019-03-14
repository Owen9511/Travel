<template>
  <div>
    <detail-banner/>
    <detail-header/>
    <div style="height:50rem"/>
  </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader
  }
}
</script>

<style lang="stylus" scoped>

</style>
