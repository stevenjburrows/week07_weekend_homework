<template>
  <div>
    <coins-list :coins='coins'></coins-list>
    <coin-details :favCoins='favouriteCoins'/>
    <coin-favourites :favCoins='favouriteCoins'/>
  </div>
</template>
 
<script>


import coinsList from './components/coinsList.vue'
import coinFavourites from './components/coinFavourites.vue'
import coinDetails from './components/coinDetails.vue'
import { eventBus } from "./main.js"

export default {
  
  data(){
    return {
      coins: [],
      favouriteCoins: [],
      coinR: null

    }
  },
  components: {
    'coins-list': coinsList,
    'coin-details' : coinDetails,
    'coin-favourites' : coinFavourites,
  },
  mounted(){
    fetch('https://api.coinpaprika.com/v1/coins')
    .then(res => res.json())
    .then(coinRes => this.coins = coinRes)

      eventBus.$on('favourited-coin', (coin)=> {
      this.favouriteCoins.push(coin);
      })

//     eventBus.$on('remove-favourited-coin', (coin)=> {
//       const coinR = coin
//       console.log(coinR);
      
//       for (var i = this.favouriteCoins.length - 1; i >= 0; --i) {
//     if (this.favouriteCoins[i].name == coinR.name) {
//         this.favouriteCoins.splice(i,1);
//     }
// }
//       // this.favouriteCoins.filter(function(el, coin) { return el.name !== coin.name; })
//       // filter(function(e) { return e.Name !== "Kristian"; });
      
//     })
  }
}
    
</script>

<style scoped>
h1 {
  color: red;
}
</style>


