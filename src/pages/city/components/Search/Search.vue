<style lang="scss" src="./Search.scss"></style>
<template>
  <div class="city-search">
    <div class="search">
      <input type="text" v-model="keyWord" placeholder="输入城市名或拼音" class="search-input">
    </div>
    <div class="search-content" ref="search" v-show="keyWord">
      <ul class="list">
        <li class="item border-bottom" 
          v-for="item in citiesList" 
          :key="item.id" 
          @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="item border-bottom" v-show="hasNoData">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import { mapMutations } from 'vuex'
export default {
  name: 'CitySearch',
  data() {
    return {
      keyWord: '',
      citiesList: [],
      timer: null
    }
  },
  computed: {
    hasNoData() {
      return !this.citiesList.length
    }
  },
  props: {
    cities: Object
  },
  watch: {
    keyWord() {
      if(this.timer) {
        clearTimeout(this.timer)
      }
      if(!this.keyWord) {
        this.citiesList = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for(let i in this.cities) {
          this.cities[i].forEach((value) => {
            if(value.spell.indexOf(this.keyWord) > -1 || value.name.indexOf(this.keyWord) >-1) {
              result.push(value);
            }
          });
        }
        this.citiesList = result
      },100)

    }
  },
  mounted() {
    this.scroll = new BScroll(this.$refs.search)
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
