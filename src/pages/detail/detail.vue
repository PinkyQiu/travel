<style lang="scss" src="./Detail.scss"></style>
<template>
  <div class="mod-detail">
    <detail-banner :sightName="sightName" :bannerImg="bannerImg" :bannerImgs="gallaryImgs"></detail-banner>
    <detail-header></detail-header>
    <div class="content">
      <detail-list :list="categoryList"></detail-list>
    </div>
  </div>
</template>

<script>
import DetailBanner from './components/Banner/Banner'
import DetailHeader from './components/Header/Header'
import DetailList from './components/List/List'
import axios from 'axios'
export default {
  name: 'Detail',
  computed: {
  },
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data() {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: '',
      categoryList: []
    }
  },
  mounted() {
    this.getDetailInfo()
  },
  methods: {
    getDetailInfo() {
      axios.get('api/detail.json?', {
        params: {
          id: this.$route.params
        }
      }).then(
        this.handleGetDataSucc
      )
    },
    handleGetDataSucc(res) {
      res = res.data
      if(res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.categoryList = data.categoryList
      }
    }
  }
}
</script>
