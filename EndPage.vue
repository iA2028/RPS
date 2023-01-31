<template>
  <div>
    <h2 class="morphing" ref="heading">Thanks for playing!</h2>
    <button class="replay-button" v-on:click="replay">Replay</button>
  </div>
</template>
<script>
import anime from 'animejs'

export default {
  methods: {
    replay() {
      this.$emit('replay')
    },
    animateText() {
      anime({
        targets: this.$refs.heading,
        translateY: [-100, 0],
        duration: 1000,
        easing: 'easeOutElastic(1, .8)',
        fontSize: '7em',
        color:'blue'
      });
    }
  },
  mounted() {
    this.animateText()
  }
}
</script>


<style scoped>
  @font-face {
    font-family: 'ArcadeClassic';
    src: url('src/assets/arcade_classic_2/ARCADECLASSIC.TTF') format('truetype');
  }
  
  h2 {
    font-family: 'ArcadeClassic';
    text-align: center;
  }
</style>