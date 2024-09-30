<script>
export default {
  data() {
    return {
      currentSection: 'play'
    }
  },
  methods: {
    showSection(section) {
      this.currentSection = section
    }
  }
}
</script>

<template>
  <div class="play" v-show="currentSection === 'play'">
    <span class="logoDot"></span>
    <p class="slogan">Show them your Quizz</p>
  </div>

  <div class="create" v-show="currentSection === 'create'">
    <span class="logoDot"></span>
    <p class="slogan">Show them a different Quizz</p>
  </div>

  <div class="library" v-show="currentSection === 'library'">
    <span class="logoDot"></span>
    <p class="slogan">Show them your last Quizz</p>
  </div>

  <div class="selected">
    <span class="dot" @click="showSection('play')" id="dot1"></span>
    <span class="dot" @click="showSection('create')" id="dot2"></span>
    <span class="dot" @click="showSection('library')" id="dot2"></span>
  </div>
</template>

<style>
.logoDot {
  height: 100px;
  width: 100px;
  background-color: #2e6464;
  border-radius: 50%;
  display: inline-block;
  text-align: center;
  margin: auto;
}
/* .logoDot later gets the icon/play button*/

.slogan {
  font-size: 1.5rem;
  color: #fff;
  text-align: center;
  padding: 1rem;
}

.play,
.create,
.library {
  border: white solid 1px;
  border-radius: 15px;

  max-width: 80%;
  min-height: 80vh;
  margin: 0 auto;
  padding: 1rem;

  display: flex;
  flex-direction: column;
  justify-content: flex-end;

  transition: all 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  /* transition for swipe function */
}

.play.previous,
.create.previous,
.library.previous {
  transform: translateX(-100%);
}
.play.active,
.create.active,
.library.active {
  transform: translateX(0%);
}
.play.next,
.create.next,
.library.next {
  transform: translateX(-100%);
}

.selected {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 5px;
}

.dot {
  height: 15px;
  width: 15px;
  background-color: #ffffff;
  border-radius: 50%;
  display: inline-block;
  text-align: center;
  margin: 5px;
}

@media (min-width: 1024px) {
  .container {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
