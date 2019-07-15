<style lang="scss" src="./Icon.scss"></style>
<template>
  <div class="mod-icon">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page,index) in pages" :key="index">
        <div class="icon" v-for="item in page" :key="item.id">
          <img :src="item.imgUrl" alt="" class="pic">
          <div class="txt">{{item.desc}}</div>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
    
  </div>
</template>

<script>
export default {
  name: 'HomeIcon',
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination'
      }
    }
  },
  computed: {
    pages() {
      const pages = [];
      this.iconList.forEach((item,index) => {
        const page = Math.floor(index / 8)
        if(!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      });
      return pages
    }
  },
  props: {
    iconList: {
      type: Array
    }
  }
}
</script>
