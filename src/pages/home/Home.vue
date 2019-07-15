<style lang="scss" src="./Home.scss"></style>
<template>
  <div class="mod-home">
    <home-header></home-header>
    <home-swiper :swiperList="swiperList"></home-swiper>
    <home-icon :iconList="iconList"></home-icon>
    <home-recommend :recommendList="recommendList"></home-recommend>
    <home-weekend :weekendList="weekendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header/Header'
import HomeSwiper from './components/Swiper/Swiper'
import HomeIcon from './components/Icon/Icon'
import HomeWeekend from './components/Weekend/Weekend'
import HomeRecommend from './components/Recommend/Recommend'
import axios from 'axios'
import { mapState } from 'vuex'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcon,
    HomeRecommend,
    HomeWeekend
  },
  mounted () {
    this.getHomeInfo()
    this.lastCity = this.city
  },
  data() {
    return {
      swiperList:[],
      iconList: [],
      recommendList: [],
      weekendList: [],
      lastCity: ''
    }
  },
  methods: {
    getHomeInfo() {
      axios.get('api/index.json?city' + this.city).then(
        this.getHomeInfoSucc
      )
    },
    getHomeInfoSucc(res) {
      res = res.data
      if(res.ret && res.data) {
        const data = res.data
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.recommendList = data.recommendList
        this.weekendList = data.weekendList
      }
    }
  },
  computed: {
    ...mapState(['city'])
  },
  activated() {
    if(this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }

}
</script>
