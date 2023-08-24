<template>
  <div id="app">
    <Home
      v-if="currentView == 'Home'" 
      :cards="cards"
      @changeCurrentView="currentView = 'AddCard'"
      @toggleCard="toggleCard"
    />
    <AddCard
      v-if="currentView == 'AddCard'" 
      @card="saveCard"
      :cards="cards"
      @changeCurrentView="currentView = 'Home'"
    />
  </div>
</template>

<script>
import * as Views from "./views";
export default {
  components: {
    AddCard: Views.AddCard,
    Home: Views.Home,
  },
  data() {
    return {
      currentView: "Home",
      title: "E-wallet",
      getTitle: "Cards",
      cards: [
        {
          cardNum: "8596 0392 3804 7469",
          cardUser: "Anna Johansson",
          expMonth: "05",
          expYear: "23",
          vend: "ninja",
          activeCard: false,
        },
        {
          cardNum: "8404 5278 0583 3604",
          cardUser: "Martin Svensson",
          expMonth: "02",
          expYear: "25",
          vend: "bitcoin",
          activeCard: false,
        },
      ],
    };
  },
  methods: {
    saveCard(card) {
      this.cards.push(card);
    },
    toggleCard(index) {
      for (const cardActivity of this.cards) {
        if (cardActivity.activeCard === true) {
          cardActivity.activeCard = false;
        }
      }
      this.cards[index].activeCard =
        !this.cards[index].activeCard;
    },
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,100&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,100&family=Poppins:wght@200&display=swap');

body {
  background-color: #dfcbcb;
  display: grid;
  place-items: center;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 400px;
  min-height: 800px;
  box-shadow: 0px 0px 32px rgba(0, 0, 0, 0.12);
  padding: 1rem;
  background-color: white;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

button {
  font-family: "PT Mono";
  font-size: 20px;
  width: 382px;
  height: 72px;
  margin-left: 4px;
  border-radius: 6px;
}
</style>