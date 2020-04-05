<template>
  <div>
      <h2>Coin list</h2>

         <form v-on:submit.prevent>
             <select name="coins" v-on:change="displayInfo" v-model="selectedCoin">
                 <option disabled selected value> -- select a coin -- </option>
                 <option v-for="(coin, index) in coins" :value="coin" :key="index" >{{coin.name}}</option>
                
             </select>

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


<style scoped>
form, h2 {
    display: flex;
    justify-content: center;
}


li {
    list-style: none;
}

</style>