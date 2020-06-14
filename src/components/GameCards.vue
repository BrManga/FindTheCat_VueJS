<template>
  <div class="game-area">
    <p>{{selectedCard}}</p>
    <h1 class="title">Where is the cat?</h1>
    <h4 class="description">Guess the card</h4>
    <div class="container">
      <appCard
        :class="{'shadow':selectedCard==card.id}"
        v-for="card in cards"
        :key="card.id"
        :card="card"
        @click.native="selectedCard=card.id"
      ></appCard>
    </div>
    <div class="container">
      <appDefaultCard :card="answer"></appDefaultCard>
    </div>
  </div>
</template>
<script>
import Card from "./Card";
import DefaultCard from "./DefaultCard";
export default {
  data: function() {
    return {
      selectedCard: "",
      answer: {},
      cards: [
        { id: 1, component: "app-cards", image: "/src/assets/card-1.jpg" },
        { id: 2, component: "app-cards", image: "/src/assets/card-2.jpg" },
        { id: 3, component: "app-cards", image: "/src/assets/card-3.jpg" },
        { id: 4, component: "app-cards", image: "/src/assets/card-4.jpg" },
        { id: 5, component: "app-cards", image: "/src/assets/card-5.jpg" }
      ]
    };
  },
  created() {
    let answer = Math.floor(Math.random() * this.cards.length);
    this.answer = this.cards[answer];
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
.shadow {
  box-shadow: 0px 5px 48px #30968f !important;
  transition: box-shadow 1s;
}
</style>