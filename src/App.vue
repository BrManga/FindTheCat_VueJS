<template>
  <transition-group name="slide" mode="out-in">
    <component key="maincompoent" :is="activeComponent" @isCorrectEvent="activeComponent=$event"></component>
    <canvas v-show="activeComponent=='appCelebrate'" id="canvas" key="canvas"></canvas>
  </transition-group>
</template>
<script>
import GameCards from "./components/GameCards";
import Failure from "./components/Failure";
import Celebrate from "./components/Celebrate";
export default {
  data: function() {
    return {
      activeComponent: "appGameCards"
    };
  },
  components: {
    appGameCards: GameCards,
    appFailure: Failure,
    appCelebrate: Celebrate
  }
};
</script>
<style>
body {
  font-family: sans-serif;
}
.slide-enter-active {
  animation: slide-in 0.7s;
}
.slide-leave-active {
  animation: slide-out 0.7s;
}
@keyframes slide-in {
  from {
    transform: translateX(-2000px);
    opacity: 0;
  }
  to {
    transform: translateX(0px);
    opacity: 1;
  }
}
@keyframes slide-out {
  from {
    transform: translateX(0px);
    opacity: 1;
  }
  to {
    transform: translateX(4000px);
    opacity: 0;
  }
}
</style>
