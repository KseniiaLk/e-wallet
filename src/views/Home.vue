<template>
    <div class="E-Wallet">
      <h1>E-Wallet</h1>
      <p>The card</p>
      <EWallet :cards="cards" @toggleCard="toggleCard" />
      <button @click="$emit('changeCurrentView')">New Card</button>
    </div>
  </template>
  
  <script>
  import EWallet from "../components/E-Wallet.vue";
  export default {
    components: { EWallet },
    props: { cards: Array },
    data() {
      return {};
    },
    methods: {
      toggleCard(index) {
        this.$emit("toggleCard", index);
      },
    },
  };
  </script>
  
  <style>
  button {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
  }
  .cards {
    display: grid;
    grid-auto-rows: auto;
    list-style-type: none;
    justify-content: center;
  }
  
  h1 {
    font-family: "Monserrat";
    font-size:40px;
    font-style: normal;
    font-weight: 700;
    line-height: 35px;
    letter-spacing: 0em;
    text-align: center;
  }
  </style>