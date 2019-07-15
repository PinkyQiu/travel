<style lang="scss" src="./List.scss"></style>
<template>
  <div class="city-list" ref="cityWrapper">
    <div>
      <div class="area">
        <h2 class="title border-topbottom">当前城市</h2>
        <div class="btn-list">
          <div class="btn-wp">
            <div class="btn">{{this.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <h2 class="title border-topbottom">热门城市</h2>
        <div class="btn-list">
          <div class="btn-wp" 
            v-for="item in hotCities" 
            :key="item.id" 
            @click="handleCityClick(item.name)">
            <div class="btn">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) in cities" :key="key" :ref="key">
        <h2 class="title border-topbottom">{{key}}</h2>
        <div class="item-list">
          <div class="item border-bottom" 
            v-for="innerItem in item" 
            :key="innerItem.id" 
            @click="handleCityClick(innerItem.name)">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'CityList',
  mounted() {
    this.scroll = new BScroll(this.$refs.cityWrapper)
  },
  props: ['cities','hotCities','letter'],
  computed: {
    ...mapState(['city'])
  },
  watch: {
    letter() {
      if(this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  methods: {
    handleCityClick(city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  }
}
</script>
