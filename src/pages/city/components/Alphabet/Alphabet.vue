<style lang="scss" src="./Alphabet.scss"></style>
<template>
  <div class="city-alphabet">
    <ul class="list">
      <li class="item" 
        v-for="item in letters" 
        :key="item" 
        @click="handleLetterClick" 
        @touchstart.prevent="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
        :ref="item">{{item}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: {
      type: Object
    }
  },
  data() {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }

  },
  computed: {
    letters() {
      const letters = []
      for(let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  updated() {
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    handleLetterClick(e) {
      this.$emit('change',e.target.innerText)
    },
    handleTouchStart() {
      this.touchStatus = true

    },
    handleTouchMove(e) {
      if(this.touchStatus) {
        if(this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 79
          const index = Math.floor((touchY - this.startY)/20)
          if(index >= 0 && index < this.letters.length) {
            this.$emit('change',this.letters[index])
          }
        },16)
      }
      
    },
    handleTouchEnd() {
      this.touchStatus = true
      
    }
  }
}
</script>
