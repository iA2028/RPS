<template>
  <div class="background" v-if="!showGame" ref="background" @mousemove="updateMousePosition" style="display: flex; align-items: center; justify-content: center;">
    <button class="play-button" v-on:click="showGame = true">{{title}}</button>
  </div>
  <gameitself v-if="showGame"></gameitself>

</template>

<script>
import Gameitself from './Gameitself.vue'

export default {
  components: {
    Gameitself
  },
  data() {
    return {
      showGame: false,
      title: "Play",
      mouseX: 0,
      mouseY: 0,
    }
  },
  computed: {
    gradient() {
      return `radial-gradient(circle at ${this.mouseX}px ${this.mouseY}px, #1c3d9a, #2f2941, #3c3449)`;
    }
  },
  methods: {
    updateMousePosition(event) {
      this.mouseX = event.clientX;
      this.mouseY = event.clientY;
      this.$refs.background.style.background = this.gradient;
    },
  }
}
</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}


 .background{
    background-color: #21123a;
    padding: 10px;
    width: 100vw;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  background-attachment: fixed;
  background-position:center;
  background: radial-gradient(circle, #21123a, #2f2941, #3c3449);
}

.play-button {
  /* button styling */
  background-color: #7e4dff;
  color: white;
  border: none;
  padding: 12px 20px;
  border-radius: 50px;
  font-size: 20px;
  font-weight: bold;
  text-transform: uppercase;
  /* button hover effect */
  transition: 0.2s all ease-in-out;
  box-shadow: 0px 0px 10px #7e4dff;
}
.play-button:hover {
  transform: scale(1.1);
}
</style>
