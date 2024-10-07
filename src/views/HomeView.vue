<script>
import CreateCard from '@/components/CreateCard.vue'

export default {
  data() {
    return {
      currentSection: 'play'
    }
  },
  components: {
    CreateCard
  },
  methods: {
    showSection(section) {
      this.currentSection = section
    }
  },
  computed: {
    activeClass() {
      return (section) => {
        return this.currentSection === section ? 'active' : ''
      }
    }
  }
}
</script>

<template>
  <div class="play" v-show="currentSection === 'play'">
    <span class="logoDot"></span>
    <p class="slogan">Show them your Quizz</p>
  </div>

  <CreateCard v-show="currentSection === 'create'" />

  <div class="library" v-show="currentSection === 'library'">
    <span class="logoDot"></span>
    <p class="slogan">Library</p>
  </div>

  <div class="selected">
    <span
      class="dot"
      :class="activeClass('play')"
      @click="showSection('play')"
      aria-label="Show Play Section"
    ></span>
    <span
      class="dot"
      :class="activeClass('create')"
      @click="showSection('create')"
      aria-label="Show Create Section"
    ></span>
    <span
      class="dot"
      :class="activeClass('library')"
      @click="showSection('library')"
      aria-label="Show Library Section"
    ></span>
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

.dot.active {
  border: 2px solid #000;
  background-color: #2e6464; /* highlighting of span.dot */
}

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

@media (max-width: 768px) {
  .logoDot {
    height: 20vw;
    width: 20vw;
  }

  .slogan {
    font-size: 4vw;
  }

  .dot {
    height: 4vw;
    width: 4vw;
  }
}

@media (min-width: 1024px) {
  .container {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
