<template>
  <div class="game-area">
    <h1 class="title">Where is the cat?</h1>
    <h4 class="description">Guess the card</h4>
    <div class="container">
      <transition-group name="rotate-all" class="card-container" appear>
        <appCard
          :class="{'shadow':selectedCard==card.id}"
          v-for="card in cards"
          :key="card.id"
          :card="card"
          @click.native="selectedCard=card.id"
        ></appCard>
      </transition-group>
    </div>
    <div class="container">
      <transition name="rotate" mode="out-in">
        <component :is="activeCard" @click.native="showCard(answer)" :card="answer"></component>
      </transition>
    </div>
  </div>
</template>
<script>
import Card from "./Card";
import DefaultCard from "./DefaultCard";
export default {
  data: function() {
    return {
      selectedCard: null,
      answer: {},
      activeCard: "app-default-card",
      cards: [
        { id: 1, component: "app-card", image: "/src/assets/card-1.jpg" },
        { id: 2, component: "app-card", image: "/src/assets/card-2.jpg" },
        { id: 3, component: "app-card", image: "/src/assets/card-3.jpg" },
        { id: 4, component: "app-card", image: "/src/assets/card-4.jpg" },
        { id: 5, component: "app-card", image: "/src/assets/card-5.jpg" }
      ]
    };
  },
  created() {
    let answer = Math.floor(Math.random() * this.cards.length);
    this.answer = this.cards[answer];
  },
  methods: {
    showCard(answer) {
      if (this.selectedCard == null) {
        alert("Please select a card");
      } else {
        this.activeCard = this.answer.component;
        setTimeout(() => {
          if (answer.id == this.selectedCard) {
            //@isCorrectEvent="activeComponent=$event" emitting to upper component the value with $event
            this.$emit("isCorrectEvent", "appCelebrate");
          } else {
            this.$emit("isCorrectEvent", "appFailure");
          }
        }, 2000);
      }
    }
  },
  components: {
    appCard: Card,
    appDefaultCard: DefaultCard
  }
};
</script>
<style scope>
.title {
  text-align: center;
  color: rosybrown;
}
.description {
  text-align: center;
  color: gray;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 50px;
}
.card-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 50px;
}
.shadow {
  box-shadow: 0px 5px 48px #30968f !important;
  transition: box-shadow 1s;
}
/* Acik kart animasyon  */
.rotate-all-enter {
}
.rotate-all-enter-active {
  animation: rotate-all ease-in-out 2s forwards;
}
.rotate-all-leave {
}
.rotate-all-leave-active {
}
@keyframes rotate-all {
  from {
    transform: rotateY(0);
  }
  to {
    transform: rotateY(1080deg);
  }
}
/* Kapali kart animasyon  */
.rotate-enter {
}
.rotate-enter-active {
  animation: rotate-in ease-in-out 1s forwards;
}
.rotate-leave {
}
.rotate-leave-active {
  animation: rotate-out ease-in-out 1s forwards;
}
@keyframes rotate-in {
  from {
    transform: rotateY(90deg);
  }
  to {
    transform: rotateY(0deg);
  }
}
@keyframes rotate-out {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(90deg);
  }
}
</style>