<style lang="scss" src="./Header.scss"></style>
<template>
  <router-link tag="div" to='/' class="detail-header">
    <div class="header-abs" v-show="showAbs">
      <span class="iconfont">&#xe682;</span>
    </div>
    <div class="header-fixed" 
      v-show="!showAbs"
      :style="opacityStyle"
    >
      <router-link to='/'>
        <div class="header-left">
          <span class="iconfont">&#xe682;</span>
        </div>
      </router-link>
      <div class="title">城市选择</div>
    </div>
  </router-link>
</template>
<script>
export default {
  name: 'DetailHeader',
  data() {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  activated() {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  computed: {
  },
  components: {
  },
  methods: {
    handleScroll() {
      const top = document.documentElement.scrollTop
      if(top > 60) {
        let opacity = top/140
        opacity = opacity > 1 ? 1 : opacity 
        this.opacityStyle = {
          opacity: opacity
        }
        this.showAbs = false
      }else {
        this.showAbs = true
      }
    }
  }
}
</script>
