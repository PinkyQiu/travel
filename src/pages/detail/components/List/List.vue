<style lang="scss" src="./List.scss"></style>
<template>
  <div class="detail-list">
    <div class="list">
      <div class="item" v-for="(item,index) in list" :key="index">
        <h2 class="title border-bottom">
          <span class="icon"></span>{{item.title}}
        </h2>
        <div class="children" v-if="item.children">
          <detail-list :list="item.children"></detail-list>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'DetailList',
  data() {
    return {
     
    }
  },
  props: ['list'],
  computed: {
  },
  components: {
  },
  
}
</script>
