<template>
  <div>
    <coins-list :coins='coins'></coins-list>
  </div>
</template>
 
<script>


import coinsList from './components/coinsList.vue'


export default {
  data(){
    return {
      coins: [],

    }
  },
  components: {
    'coins-list': coinsList,
  },
  mounted(){
    fetch('https://api.coinpaprika.com/v1/coins')
    .then(res => res.json())
    .then(coinRes => this.coins = coinRes)

  }
}
</script>

<style scoped>
h1 {
  color: red;
}
</style>


