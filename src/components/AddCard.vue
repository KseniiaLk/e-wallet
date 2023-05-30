<template>
  <main>
      <div>
    <h2>
      New Card
    </h2>
    <p v-for="error in errors" :key="error">
      <b class="error" v-if="errors.length"> {{errors}} </b> </p>
      <div class="cardWrapper" v-bind:style="cardColors">
      <div class="logo">
      <img :src="cardInfo.vendor.cardWifi">
      <img :src="cardInfo.vendor.cardLogo">
      </div>
       <img class="chip" :src="cardInfo.vendor.cardChip">
       <h1>{{sepCardNum}}</h1>
       <div class="card">
      <div class="nameInfo">
      <p class="name">Name: <br>{{cardInfo.cardName}} </p>
      <p class="info">Year/Month <br>{{cardInfo.cardMonth}}/{{cardInfo.cardYear}}</p>
      </div>
  </div>
</div>
  
    <form  @submit.prevent="sendCard" class="styled-form">
        <label for="cardNum">Card number</label><br>

        <input v-model="cardInfo.cardNum" type="text" id="cardNum" maxlength="16" class="input-field"><br>
        <label for="cardName">Name</label><br>
        <input v-model="cardInfo.name" type="text" id="cardHolder" placeholder="Name Surname" class="input-field"><br>
            <label for="cardMonth">Month</label>
            <select name="cardMonth" v-model="cardInfo.cardMonth" class="select-field">
              <option v-for="cardMonth in cardMonths" :key="cardMonth" value:value="cardMonth">
                {{ cardMonth }}
              </option>
            </select>
            <label for="cardYear">Year</label>
            <select name="cardYear" v-model="cardInfo.year" class="select-field">
              <option v-for="cardYear in cardYears" :key="cardYear" name="cardYear">
                {{ cardYear }}
              </option>
            </select>
        <label for="vendor">Vendor</label>
        <select id="vendor" name="vendor" v-model="cardInfo.vendor" class="select-field">
          <option v-for="vendor in vendor" :key="vendor.name" :name="vendor" :value="vendor">
            {{ vendor.name }}
          </option>
        </select>
          <button class="button"> Add card</button>
         </form>
         </div>
    </main>
  </template>
  
  <script>
  export default {
      data() { return {
          cardInfo: {
            cardNum: "", 
            cardName: "", 
            cardInfo: "",
            vendor: {
            name: 'Evil Corp',
            backgroundColor: '#D0D0D0',
            color: 'black',
            cardChip: require('../assets/chip.svg'),
            cardLogo: require('../assets/bitcoin.svg'),
            cardWifi: require('../assets/wifi_white.svg'),
          }
          },  
          months: ['01', '02', '03', '04', '05', '06', '07', '08', '09', '10', '11', '12'],
          years: [ '2024', '2025', '2026', '2027'],
          vendor: [
          {
            name: 'Bitcoin Inc',
            backgroundColor: '#FFAE34',
            color: 'black',
            cardChip: require('../assets/chip.svg'),
            cardLogo: require('../assets/bitcoin.svg'),
            cardWifi: require('../assets/wifi_white.svg'),
          },
          {
            name: 'Ninja Bank',
            backgroundColor: '#222222',
            color: 'black',
            cardChip: require('../assets/chip.svg'),
            cardLogo: require('../assets/ninja.svg'),
            cardWifi: require('../assets/wifi_white.svg'),
          },
          {
            name: 'Block Chain Inc',
            backgroundColor: '#8B58F9',
            color: 'black',
            cardChip: require('../assets/chip.svg'),
            cardLogo: require('../assets/blockchain.svg'),
            cardWifi: require('../assets/wifi.svg'),
            
          },
          {
            name: 'Evil Corp',
            backgroundColor: '#F33355',
            color: 'black',
            cardChip: require('../assets/chip.svg'),
            cardLogo: require('../assets/evil.svg'),
            cardWifi: require('../assets/wifi_white.svg'),
          },
        ],
        errors: [],
      }
      },
      computed: {
      cardColors() {
        return {
          backgroundColor: this.cardInfo.vendor.backgroundColor,
          color: this.cardInfo.vendor.color,
      };
  },  
  sepCardNum() {
      let output = ""
      for( let i = 0; i < this.cardInfo.cardNum.length; i++) {
        if  ( (i+1) % 4 == 0) {
          output += this.cardInfo.cardNum[i] + ' '; 
      } else { output += this.cardInfo.cardNum[i];
      }
    } return output
},
    },
      methods: {
          sendCard(){
            this.validate()
            if (this.errors.length == 0) {
              this.$emit('sendCard', {...this.cardInfo})
                this.$emit('viewChange');
            }
          },  
          validate() {
            if (this.cardInfo.cardNum.length != 16) {
          this.errors.push('must contain 16 digits')
            }
            if (this.cardInfo.name.length == 0) {
              this.errors.push('name required')
            } 
          } 
      }
  }
  </script>
  
  <style scoped>
  .cardWrapper {
  width: 390px;
  height: 240px; 
  border-radius: 3%;
  }
  
  h1 {
    margin: 1rem;
  }
  
  .logo {
    display: flex;
  flex-direction: row;
  width: 100%;
  justify-content: space-between;
  height: 4rem;
  }
  
  .card {
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 10px;
  margin-bottom: 20px;
}
  .nameInfo {
    display: flex;
  flex-direction: row;
  width: 100%;
  justify-content: space-between;
  }
  
  .chip {
    margin-left: 1rem;
  }
  
  .name {
    margin-left: 1rem;
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  .info {
    margin-right: 1rem;
    font-style: italic;
    margin-bottom: 5px;
  }
  .styled-form {
  display: flex;
  flex-direction: column;
  font-family: Arial, sans-serif;
  margin: auto;
  width: 400px;
}

.input-field {
  width: 300px;
  padding: 5px;
  margin-bottom: 10px;
}

.select-field {
  width: 200px;
  padding: 5px;
  margin-bottom: 10px;
}
  .button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.button:hover {
  background-color: #45a049;
}

.button:active {
  background-color: #3c9039;
}
  .error {
    color: rgb(230, 165, 36);
  }
  
  </style>