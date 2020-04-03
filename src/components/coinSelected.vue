<template>
  <div>
      <span von-on:change="displayInfo" > </span>
      
  </div>
</template>

<script>
import coinsList from "./coinsList.vue"
export default {
    name: "coin-selected",
    props: ['coin'],
    components: {
        "coins-list" : oinsList

    },
    methods: {
        displayInfo: function() {
            eventBus.$emit("coin-selected", this.coin)
        }
    }

}
</script>

<style>

</style>