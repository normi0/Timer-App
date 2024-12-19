<template>
  <div id="app">
    <h1>Timer Vue Web Page</h1>
    <!-- Challenge Popup -->
    <ChallengePopup v-if="isSectionVisible" @clickMe="stopChallenge">
      <p>Click Me!!</p>
    </ChallengePopup>
    <!-- Result Popup -->
    <ResultPopup v-if="result">
      <p>Time Taken: {{ timeTaken }} ms</p>
      <p>{{ performanceMessage }}</p>
      <button @click="restartChallenge">Restart</button>
    </ResultPopup>
    <!-- Start Button -->
    <button
      class="starter-btn"
      @click="startChallenge"
      v-if="!isSectionVisible"
    >
      Start
    </button>
  </div>
</template>

<script>
import ChallengePopup from "./components/ClickSection.vue";
import ResultPopup from "./components/Result.vue";

export default {
  name: "App",
  components: {
    ChallengePopup,
    ResultPopup,
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
      if (this.timeTaken < 500) return "You are fast! 🏃‍♂️";
      else if (this.timeTaken < 1000) return "Not bad! 🚶‍♀️";
      else return "You are slow! 🐢";
    },
  },
  methods: {
    startChallenge() {
      this.isSectionVisible = false;
      this.result = false;
      this.timeTaken = null;
      const delay = Math.floor(Math.random() * 3000) + 1000;

      setTimeout(() => {
        this.startTime = Date.now();
        this.isSectionVisible = true;
      }, delay);
    },
    stopChallenge() {
      this.timeTaken = Date.now() - this.startTime;
      this.result = true;
      this.isSectionVisible = false;
    },
    restartChallenge() {
      this.isSectionVisible = false;
      this.result = false;
    },
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  background-color: #f5f5f5;
  display: flex;
  flex-direction: column;
}
h1 {
  padding: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  border-radius: 15px;
  height: 40vh;
  background: lightcoral;
  color: white;
  text-align: center;
  box-shadow: 0px 5px 10px gray;
  z-index: 1; /* Lower z-index than the popup */
}
button {
  height: 10vh;
  width: 20vw;
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
  justify-content: space-evenly;
}
</style>
