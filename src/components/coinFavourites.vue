<template>
  <div>
      <h2>Favourite coins</h2>
    <ul>
        <li v-for="(coin, index) in favCoins" :coin="coin" :key="index">
            <h2>Name:  {{coin.name}}</h2>
            <p>ID: {{coin.id}}</p>
            <p>Type: {{coin.type}}</p>
            <p>Still Active? {{coin.is_active}}</p>
            <!-- <button v-on:click="removeFromFavourites">Remove from Favourites </button> -->
        </li>
        
    </ul>

  </div>
</template>

<script>
import { eventBus } from "../main.js"
export default {
    name: 'coin-favourites',
    props: ['favCoins'],
    // methods: {
    //     removeFromFavourites: function(){
    //       eventBus.$emit( 'remove-favourited-coin', this.coin )
    //     }
    // }
}
</script>

<style scoped>
 li {
     list-style: none;
     background-color: lightgray;
     display: inline-block;
     padding: 0.75rem;
     margin: 0.75rem;

 };
</style>
