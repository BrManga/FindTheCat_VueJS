<template>
  <component :is="activeComponent"></component>
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
</style>
