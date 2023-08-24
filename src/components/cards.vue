<template>
    <div>
      <section
        class="card"
        id="Cards"
        @click="$emit('activeCard', index)"
        :class="card.vend"
      >
        <div class="card-needed card-choose" :class="card.cardColor">
          <img class="card-w" src="../assets/wifi_white.svg" />
          <img class="card-chip" src="../assets/chip.svg" />
          <img class="card-logo" v-if="card.vend" :src="require(`../assets/${card.vend}.svg`)" />
          <p class="card-n">{{ card.cardNum }}</p>
          <div class="card-space-75">
            <span class="card-l">Name</span>
            <p class="card-i" @input="onlyLetters">{{ card.cardUser }}</p>
          </div>
          <div>
            <div class="card-space-25">
              <span class="card-l">Valid </span>
              <p class="card-i">
                {{ card.expMonth }} / {{ card.expYear }}
              </p>
            </div>
          </div>
        </div>
      </section>
    </div>
  </template>
  
  <script>
  export default {
    props: { card: Object, index: Number},
    methods: {
      onlyLetters() {
        this.card.cardUser = this.card.cardUser.replaceAll(/[^a-zA-Z\s]+/g, "").toUpperCase();
      },
    },
  };
  </script>
  
  <style lang="scss">
 @import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,100&display=swap');
  * {
    box-sizing: border-box;
    font-style: normal;
    font-weight: 200;
    font-display: swap;
  }
  
  html,
  body {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
  }
  
  .card {
    width: 320px;
    height: 200px;
    perspective: 600px;
    display: inline-block;
    -webkit-perspective: 600px;
    -moz-perspective: 600px;
    border-radius: 8px;
    background: #c9c6c6;
  }
  
  .card-choose {
    top: 0;
    position: absolute;
    left: 0;
    display: inline-block;
    width: 300px;
    height: 190px;
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    border-radius: 8px;
  }
  
  .vend {
    background: rgb(234, 232, 232);
  }
  
  .card-needed {
  padding: 18px;
}

  .card-logo {
    height: 30px;
    position: absolute;
    top: 18px;
    right: 18px;
  }
  
  .card-w {
    height: 40px;
    left: 0;
    position: absolute;
    margin-left: 1.0rem;
    margin-top: -0.5rem;
  }
  
  .card-chip {
    height: 30px;
    left: 0;
    position: absolute;
    margin: 1.5rem;
  }
  
  .card-n{
    display: block;
    width: 100%;
    word-spacing: 3px;
    font-size: 15px;
    letter-spacing: 2px;
    color: #fff;
    text-align: left;
    margin-bottom: 20px;
    margin-top: 20px;
    padding-left: 60px;
  }
  
  .card-space-75 {
    float: left;
    padding-top: 35px;
  }
  
  .card-space-25 {
    float: right;
    padding-top: 35px;
  }
  
  .card-l {
    font-size: 12px;
    text-transform: uppercase;
    color: rgba(101, 96, 96, 0.8);
    letter-spacing: 1.5px;
  }
  
  .card-i {
    padding-bottom: 10px;
    margin-top: 5px;
    font-size: 14px;
    line-height: 18px;
    color: #f8f4f4;
    letter-spacing: 1px;
    text-transform: uppercase;
    position: absolute;
    bottom: 0;
  }
  
  .bitcoin {
    background-color: #ffae34;
  }
  .ninja {
    background-color: #222222;
  }
  .blockchain {
    background-color: #8b58f9;
  }
  .evil {
    background-color: #f33355;
  }
  </style>