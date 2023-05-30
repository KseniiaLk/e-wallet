<template>
    <main>
    <div>
      <h1> E-Wallet</h1>
      <h5>Active card</h5>
      <CardCard class="activeCard" v-if="isActive" v-bind:card="isActive"/>
    </div>
    <div class="cardGet">
      <CardCard v-for="card in cards" :key ="card.id" v-bind:card="card" @activeCard="activeCard" />
      <button class="bottom" @click="changeView">Add new Card </button>
      </div>
      </main>
    </template>
    
    <script>
    import CardCard from './CardCard.vue'
    
    export default {
        data(){ return {
            isActive: null
        }
        },
        components: {CardCard},
        props: ['cards'],
        methods: {
            changeView() {
            this.$emit('viewChange');
        }, 
    activeCard(card) {
    this.isActive = card
    this.$emit('activeCard', this.isActive)
    }
        },
    }
    </script>
    
    
    <style scoped>
    .activeCard{
    margin-bottom: 3rem;
    margin-top: 1rem;
    }
    .cardGet{
    display: grid;
    grid-auto-rows: 2rem;
    height: 80px;
    background-color: rgb(202, 195, 194);
    }
    
    .bottom {
    position: relative;
    width: 382px;
    height: 90px;
    top: 18rem;
    }
    </style>