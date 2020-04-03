<template>
  <div>
      <h2>Coin list</h2>
      <ul>
         <li v-for="(coin, index) in coins" :coin="coin" :key="index">{{coin.name}}</li>
      </ul>

  </div>
</template>

<script>
export default {
    name: 'coins-list',
    props: ['coins'],


}
</script>
console.log(beers)
<style scoped>

li {
    list-style: none;
}

</style>