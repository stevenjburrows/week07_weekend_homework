<template>
  <div>
    <coins-list :coins='coins'></coins-list>
    <coin-details :favCoins='favouriteCoins'/>
  </div>
</template>
 
<script>


import coinsList from './components/coinsList.vue'
import coinDetails from './components/coinDetails.vue'
import { eventBus } from "./main.js"

export default {
  
  data(){
    return {
      coins: [],
      favouriteCoins: []

    }
  },
  components: {
    'coins-list': coinsList,
    'coin-details' : coinDetails,
  },
  mounted(){
    fetch('https://api.coinpaprika.com/v1/coins')
    .then(res => res.json())
    .then(coinRes => this.coins = coinRes)

       eventBus.$on('favourited-coin', (coin)=> {
      this.favouriteCoins.push(coin);
    })
    

  }
}
</script>

<style scoped>
h1 {
  color: red;
}
</style>


