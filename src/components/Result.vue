<template>
  <div class="result">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "ResultPopup",
};
</script>
<style scoped>
.result-popup {
  width: 300px;
  height: 200px;
  background-color: lightgreen;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  border-radius: 10px;
  box-shadow: 0px 5px 10px rgb(197, 196, 196, 0.2);
  font-size: 20px;
  font-weight: bold;
  text-align: center;
  gap: 10px;
}
button {
  padding: 10px 20px;
  background-color: purple;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}
button:hover {
  background-color: darkorchid;
}
</style>
