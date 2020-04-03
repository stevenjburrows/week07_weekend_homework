<template>
  <div v-if="this.coinD">
      <h1>Coin Details</h1>
    <h2>Name:  {{this.coinD.name}}</h2>
    <p>ID: {{this.coinD.id}}</p>
    <p>Type: {{this.coinD.type}}</p>
    <p>Still Active? {{this.coinD.is_active}}</p>
    <Button v-if="!favCoins.includes(this.coinD)" v-on:click="addToFavourites">Add to Favourites</Button>

  </div>
</template>

<script>
import { eventBus } from "../main.js";
export default {
    name: 'coin-details',
    props: ['favCoins'],
    

   data() {
        return{
            coinD: {}
        }
    },


    mounted() {
        eventBus.$on('coin-selected', (selectedCoin) => {
            this.coinD = selectedCoin            
        })

        
    },
        methods: {
        addToFavourites: function(){
          eventBus.$emit( 'favourited-coin', this.coinD )
    }
  }

}
</script>


<style>

</style>