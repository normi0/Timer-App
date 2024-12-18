<template>
  <div id="app">
    <h1>Timer Vue Web Page</h1>
    <challengesection v-if="isSectionVisible" @clickMe="stopChallenge">
      <p>click Me!!</p>
    </challengesection>
    <div v-if="result" class="backdrop">
      <result>
        <p>Time Taken :{{ timeTaken }}ms</p>
        <p>{{ performanceMessage }}</p>
        <button @click="resetChallenge" class="retry-btn">Retry</button>
      </result>
    </div>
    <button
      class="starter-btn"
      @click="startChallenge"
      v-if="!isSectionVisible"
    >
      start
    </button>
  </div>
</template>

<script>
import result from "./components/Result.vue";
import challengesection from "./components/ClickSection.vue";
export default {
  name: "App",
  components: {
    challengesection,
    result,
  },
  data() {
    return {
      isSectionVisible: false,
      startTime: null,
      timeTaken: null,
      result: false,
    };
  },
  computed: {
    performanceMessage() {
      if (this.timeTaken < 500) {
        return "You are fast! 🏃‍♂️";
      } else if (this.timeTaken < 1000) {
        return "Not bad! 🚶‍♀️";
      } else {
        return "You are slow! 🐢";
      }
    },
  },
  methods: {
    startChallenge() {
      this.isSectionVisible = false;
      this.result = false;
      this.timeTaken = null;
      const delay = Math.floor(Math.random() * 3000) + 1000;

      setTimeout(() => {
        this.startChallenge = Date.now();
        this.isSectionVisible = true;
      }, delay);
    },
    stopChallenge() {
      this.timeTaken = Date.now() - this.startChallenge;
      this.result = true;
      this.isSectionVisible = false;
    },
    resetChallenge() {
      window.location.reload();
    },
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: #f5f5f5;
}
h1 {
  text-align: center;
  margin: 20px 0;
}

/* h1 {
  width: 60vw;
  height: 40vh;
  border-radius: 10px;
  background: blue;
  color: white;
  display: flex;
  justify-content: center;
  align-content: center;
  text-align: center;
  box-shadow: 0px 5px 5px gray;
} */
.starter-btn,
.retry-btn {
  height: 10vh;
  width: 20vw;
  font-size: 18px;
  cursor: pointer;
  margin-top: 20px;
  border-radius: 15px;
  border: none;
  background-color: purple;
  color: white;
  box-shadow: 0px 5px 5px gray;
  font-size: 18px;
}
#app {
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.BackDrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-content: center;
  z-index: 10;
}
</style>
