<template>
    <div id="addCard">
      <header>
        <h1>
          Add a card
        </h1>
        <p>New card</p>
        <Cards :card="card" />
      </header>
      <main>
        <form action="" method="post" @submit.prevent="submit">
          <p>
            <label for="cardNum">Number</label>
            <br />
            <input
              id="cardNumber"
              type="num"
              name="cardNumber"
              v-model="card.cardNum"
              :maxlength="16"
              @input="card.cardNum = card.cardNum.slice(0, 16)"
            />
          </p>
  
          <p>
            <label for="cardUser">Name</label>
            <br />
            <input
              id="cardUser"
              type="text"
              name="cardUser"
              v-model="card.cardUser"
  
            />
          </p>
  
          <p>
            <label for="month">Month</label>
            <br />
            <select name="month" id="month" v-model="card.expMonth">
           <option v-for="month in 12" :key="month">{{ month }}</option>
            </select>
          </p>
  
          <p>
            <label for="year">YEAR</label>
            <br />
            <select name="year" id="year" v-model="card.expirationYear">
         <option v-for="year in 6" :key="year">{{ String(new Date().getFullYear() + year - 1).slice(-2) }}</option>
        </select>
          </p>
  
          <p>
            <label for="vend">Vendor</label>
            <br />
            <select id="vend" name="vend" v-model="card.vend">
            <option disabled selected value>-- select an option --</option>
                      <option value="" disabled selected hidden></option>
                      <option value="bitcoin">Bitcoin</option>
                      <option value="ninja">Ninja</option>
                      <option value="blockchain">Blockchain</option>
                      <option value="evil">Evil</option>
            </select>
          </p>
        <button @click="$emit('changeCurrentView'), submit()" :cards="cards" type="submit">Add card</button>
        </form>
      </main>
    </div>
  </template>
  
  <script>
  import Cards from "../components/cards.vue";
  export default {
    props: { cards: Array },
    components: { Cards },
    data() {
      return {
        card: {
          cardNum: "",
          cardUser: "",
          expMonth: "",
          expYear: "",
          vendor: "",
          activeCard: false,
        },
      };
    },
    methods: {
      submit() {
        this.$emit("card", { ...this.card });
      },
    },
  };
  </script>
  
  <style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,100&family=Poppins:wght@200&display=swap');
  * {
    box-sizing: border-box;
    font-family: "Monserrat";
    font-style: normal;
    font-weight: 100;
    font-display: swap;

  }
  
  html,
  body {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
  }
  </style>