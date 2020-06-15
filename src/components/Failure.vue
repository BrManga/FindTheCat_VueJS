<template>
  <div class="container">
    <h1>Wrong Answer!!!</h1>
    <button @click="newGame">New Game</button>
  </div>
</template>
<script>
export default {
  methods: {
    newGame() {
      this.$emit("isCorrectEvent", "appGameCards");
    }
  }
};
</script>
<style scoped>
.container {
  position: absolute;
  margin: 0;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: darkred;
}
.container h1 {
  text-align: center;
  font-size: 333%;
  color: white;
}
.container button {
  cursor: pointer;
  width: 200px;
  color: darkred;
  border: 2px solid black;
  font-size: 150%;
}
.container button:hover {
  transition: 0.5s;
  color: rgb(198, 223, 198);
  background: lightsalmon;
}
</style>>

