<template>
    <div>
      <div v-for="(card, item) in cards" :key="card.cardNum[item]">
        <Card v-if="card.activeCard" :card="card" :index="item" />
      </div>
      <div v-for="(card, item) in cards" :key="card.cardNum">
        <Card
          :card="card"
          @activeCard="toggleCard"
          :index="item"
          class="cards"
        />
      </div>
    </div>
  </template>
  
  <script>
  import Card from "./cards.vue";
  export default {
    components: { Card },
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
  
  <style lang="scss">
  .cards{
    display:grid;
    grid-auto-rows: auto;
    height: 80px;
  }
  </style>