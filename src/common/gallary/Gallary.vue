<style lang="scss" src="./Gallary.scss"></style>
<template>
  <div class="common-gallary" @click.prevent.stop="handleGallaryClick">
    <div class="wp">
      <div class="swiper-wp">
        <swiper :options="swiperOption">
          <swiper-slide v-for="(item,index) in imgs" :key="index">
            <img :src="item" alt="" class="pic">
          </swiper-slide>
          <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
  </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'CommonGallary',
  props: ['imgs'],
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        loop: true,
        observer:true,
        observeParents:true
      }
    }
  },
  methods: {
    handleGallaryClick() {
      this.$emit('close')
    }
  }
}
</script>
