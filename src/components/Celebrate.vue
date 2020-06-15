<template>
  <div class="container">
    <h1>Congrats!!!</h1>
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
}
.container h1 {
  text-align: center;
  font-size: 333%;
  color: rgb(10, 85, 7);
}
.container button {
  cursor: pointer;
  width: 200px;
  color: rgb(39, 44, 8);
  border: 2px solid black;
  font-size: 150%;
}
.container button:hover {
  transition: 0.5s;
  color: rgb(198, 223, 198);
  background: rgb(43, 110, 29);
}
</style>>

