<style lang="scss" src="./Swiper.scss"></style>
<template>
  <div class="swiper-wp">
    <swiper :options="swiperOption" v-if="showSwiper">
      <swiper-slide v-for="item in swiperList" :key="item.id">
        <img :src="item.imgUrl" alt="" class="pic">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
    }
  },
  props: {
    swiperList: {
      type: Array
    }
  },
  computed: {
    showSwiper() {
      return this.swiperList.length
    }
  },
  mounted() {
  }
}
</script>
