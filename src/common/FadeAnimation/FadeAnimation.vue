<style lang="scss" src="./FadeAnimation.scss"></style>
<template>
  <transition>
    <slot></slot>
  </transition>
</template>
<script>
export default {
  name: 'fade',
  data() {
    return {
    }
  },
  methods: {
  }
}
</script>
