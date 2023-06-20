<script>
  export default {
    data: () => ({
      count: 0,
      counterTitle: "Counter Standard",
      incrementAmount: 10,
    }),

    computed: {
      displayTitle() {
        if(this.count > 20) {
          return "Counter Standard - Very Long"
        } else {
          return "Counter Standard"
        }
      },
      optimizedIncrementAmount() {
        return this.displayTitle.length * this.incrementAmount;
      }
    },
    methods: {
      incrementCount(newAmount, event) {
        console.log(newAmount);
        console.log(event);
        this.count += this.incrementAmount
      }
    },
  }
  
</script>

<template>
  <h1>{{ displayTitle }}</h1>
  <p>{{ count }}</p>
  <button v-on:click="incrementCount">Increment Count</button>
  <h1>{{ incrementAmount }}</h1>
  <div>
    <label for="incrementAmount">incrementAmount</label>
    <input type="number" v-model="incrementAmount">
  </div>
</template>