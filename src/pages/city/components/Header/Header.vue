<style lang="scss" src="./Header.scss"></style>
<template>
  <div class="city-header">
    <router-link to='/'>
      <div class="header-left">
        <span class="iconfont">&#xe682;</span>
      </div>
    </router-link>
    <div class="title">城市选择</div>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>
