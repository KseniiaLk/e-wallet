<template>
  <main class="app">
  <Wallet v-bind:cards="cards" v-if="currentView == 'wallet'" @viewChange="changeView" />
  <AddCard v-else @viewChange="changeView" @sendCard="newCard"/>
</main>
</template>

<script>
import Wallet from './components/Wallet.vue'
import AddCard from './components/AddCard.vue'

export default {
components: {Wallet, AddCard},
data() { return {
cards: [
  {
  id: 1,
   cardName: 'Anna Fredriksson',
    cardNum:"9485 0193 4839 2019",
     cardYear: 26,
      cardMonth:12,
        vendor: { 
        name: 'Ninja Bank',
        backgroundColor: '#ffae34',
        color: 'black',
        cardChip: require('./assets/chip.svg'),
        cardLogo: require('./assets/ninja.svg'),
        cardWifi: require('./assets/wifi_white.svg'),
       
      }},
  {
    id: 2, 
    cardName: 'Gustav Nisson',
     cardNum: "8402 4039 2029 9304", 
     cardYear: 25,
      cardMonth:10,
       vendor: {
        name: 'Block Chain Inc',
        backgroundColor: '#8b58f9',
        color: 'black',
        cardChip: require('./assets/chip.svg'),
        cardLogo: require('./assets/blockchain.svg'),
        cardWifi: require('./assets/wifi_white.svg'),
      }},
  {
    id: 3, 
    cardName: 'Greta Andersson',
     cardNum:"3922 0294 2049 2817",
      cardYear: 27,
       cardMonth:11,
        vendor:  {
        name: 'Evil Corp',
        backgroundColor: '#f33355',
        color: 'white',
        cardChip: require('./assets/chip.svg'),
        cardLogo: require('./assets/evil.svg'),
        cardWifi: require('./assets/wifi_white.svg'),
    }
  }],
currentView: 'wallet',
}
},
methods: {
  newCard(newInfo) {
  this.cards.push(newInfo) 
  }, 
}, 
changeView() {
  if (this.currentView == 'wallet') {
    this.currentView = 'addCard';
  } else {
    this.currentView = 'wallet';
  }
},
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300;600&display=swap');
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&display=swap');

.app {
display: flex;
align-content: center;
margin: auto;
width: 414px;
text-transform: uppercase;
}
h2 {
font-family: 'Source Sans Pro', sans-serif;
text-align: center;
}
h3 {
color:  #1a1717;
opacity: 60%;
text-align: center;
font-family: 'Source Sans Pro', sans-serif;
}
.button {
  font-family: 'PT Mono', monospace;
  font-size: 1.5rem;
  font-weight: 500;
  border: 2px solid;
  border-radius: 6px;
  padding: 1rem;
  color: black;
  background-color: rgb(129, 125, 125);
  cursor: pointer;
}

.button:hover {
  background-color: #f0f0f0;
}

.button:active {
  background-color: #e0e0e0;
}
</style>