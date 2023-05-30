<template>
    <div class="card" v-bind:style="cardColors" @click="$emit('activeCard', card)"> 
      <div class="logoW">
      <img :src="card.vendor.cardWifi">
      <img :src="card.vendor.cardLogo">
      </div>
       <img class="cardChip" :src="card.vendor.cardChip">
       <h1>{{card.cardNum}}</h1>
      <div class="cardNI">
      <div class="cardName">Name <br>{{card.cardName}} </div>
      <div class="cardInfo">Year/Month <br>{{card.cardYear}}/{{card.cardMonth}}</div>
      </div>
  </div>
  </template>
  
  <script >
  export default {
  props: ['card'],
  computed: {
      cardColors() {
        return {
          backgroundColor: this.card.vendor.backgroundColor,
          color: this.card.vendor.color,
      }
  },
  },
      }
  
  </script>
  
  <style scoped>
  
  .card {
  width: 382px;
  height: 241px; 
  -webkit-perspective: 600px;
  -moz-perspective: 600px;
  perspective: 600px;
  display: inline-block;
  border-radius: 8px;
  filter: drop-shadow(0px 0px 16px rgba(0, 0, 0, 0.12));
  
  }
  
  h1 {
   text-align: center;
   margin: 0.5rem;
  }
  
  .logoW {
   display: flex;
   flex-direction: row;
   width: 100%;
   justify-content: space-between;
   height: 40px;
  }
  
  .cardChip {
    margin-top: 1rem;
    margin-left: 1rem;
  }
  
  .cardNI {
   display: flex;
   flex-direction: row;
   width: 100%;
   justify-content: space-between;
   margin-top: 1rem;
   color: #fff;
  }
  
  .cardName {
    margin-left: 1rem;
  }
  
  .cardInfo {
    margin-right: 1rem;
  }
  
  </style>