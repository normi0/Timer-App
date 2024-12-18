<template>
  <div class="BackDrop">
    <div class="challengesection" @click.self="clickMe">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    clickMe() {
      this.$emit("clickMe");
    },
  },
};
</script>
<style scoped>
.BackDrop {
  display: flex;
  align-content: center;
  justify-content: center;
  position: relative;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(137, 136, 136, 0.5);
  z-index: 11;
}
.challengesection {
  width: 300px;
  height: 200px;
  background-color: lightblue;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  font-size: 20px;
  font-weight: bold;
  text-align: center;
}
</style>
