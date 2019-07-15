<style lang="scss" src="./Weekend.scss"></style>
<template>
  <div class="mod-weekend">
    <h2 class="title">周末去哪儿</h2>
    <ul class="list">
      <li class="item" v-for="item in weekendList" :key="item.id">
        <div class="item-img">
          <img :src="item.imgUrl" alt="" class="pic">
        </div>
        <div class="txt-wp">
          <p class="item-title">{{item.title}}</p>
          <p class="desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  data() {
    return {
    }
  },
  props: {
    weekendList: {
      type: Array
    }
  }
}
</script>
