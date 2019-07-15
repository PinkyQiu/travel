<style lang="scss" src="./Banner.scss"></style>
<template>
  <div class="detail-banner" @click="handleBannerClick">
    <img :src="bannerImg" alt="" class="banner-img">
    <div class="banner-info">
      <div class="title">{{this.sightName}}</div>
      <div class="num"><span class="iconfont">&#xe634;</span>{{this.bannerImgs.length}}</div>
    </div>
    <fade-animation>
      <common-gallary 
        :imgs="bannerImgs" 
        @close="handleGallaryClose"
        v-show="showGallary"></common-gallary>
    </fade-animation>
  </div>
</template>
<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/FadeAnimation/FadeAnimation'
export default {
  name: 'DetailBanner',
  data() {
    return {
      showGallary: false
    }
  },
  computed: {
  },
  components: {
    CommonGallary,
    FadeAnimation
  },
  methods: {
    handleBannerClick() {
      this.showGallary = true
    },
    handleGallaryClose() {
      this.showGallary = false
      console.log(this.showGallary)
    }
  },
  props: ['sightName','bannerImg','bannerImgs']
}
</script>
