<template>
  <div>
      <h2>Coin list</h2>
      <!-- <ul>
         <li v-for="(coin, index) in coins" :coin="coin" :key="index">{{coin.name}}</li>
         </ul> -->
         <form v-on:submit.prevent>
             <select name="coins" v-on:change="displayInfo" v-model="selectedCoin">
                 <option disabled selected value> -- select a coin -- </option>
                 <option v-for="(coin, index) in coins" :value="coin" :key="index" >{{coin.name}}</option>
                
             </select>
              <!-- <button v-on:click="displayInfo" >select</button> -->
            <!-- <coin-selected v-if="coin"> 
                <p>{{coin.name}}</p>
                 </coin-selected> -->
         </form>
    

  </div>
</template>

<script>
import { eventBus } from "../main.js";
export default {
    name: 'coins-list',
    props: ['coins'],
    data() {
        return{
            selectedCoin: null
        }
    },
    methods: {
        displayInfo: function() {
            eventBus.$emit("coin-selected", this.selectedCoin)
        }
    }
}
</script>
console.log(beers)
<style scoped>

li {
    list-style: none;
}

</style>