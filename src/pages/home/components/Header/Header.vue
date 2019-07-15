<style lang="scss" src="./Header.scss"></style>
<template>
  <div class="mod-header">
    <div class="header-left">
      <span class="iconfont">&#xe682;</span>
    </div>
    <div class="header-input"><span class="iconfont icon-search">&#xe611;</span>输入城市/景点/游玩城市</div>
    <router-link to='/city'>
      <div class="header-right">{{this.city}}<span class="iconfont icon-down">&#xe665;</span></div>
    </router-link>
    
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>
