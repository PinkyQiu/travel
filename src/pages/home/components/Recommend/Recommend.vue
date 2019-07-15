<style lang="scss" src="./Recommend.scss"></style>
<template>
  <div class="mod-recommend">
    <h2 class="title">热销推荐</h2>
    <ul class="list">
      <router-link 
        :to="'/detail/'+ item.id" 
        tab="li"
        class="item border-bottom"
        v-for="item in recommendList" 
        :key="item.id">
        <div class="item-img">
          <img :src="item.imgUrl" alt="" class="pic">
        </div>
        <div class="txt-wp">
          <p class="item-title">{{item.title}}</p>
          <p class="desc">{{item.desc}}</p>
          <button class="btn">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  data() {
    return {
    }
  },
  props: {
    recommendList: {
      type: Array
    }
  }
}
</script>
