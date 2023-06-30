<script>
  export default {
    props: {
      // using computed property
      user: {
        type: Object,
        required: true
      }
      // instead of passing the entire onject you can just pass what you need.
      // name: {
      //   type: String,
      //   default: "John Doe",
      // },
      // food: {
      //   type: String,
      //   default: "Sushi",
      // }
    },
    emits: ["change-name"],
    // another emit option if you don't want to emit from btn
    methods: {
      tellParentChangeName() {
        this.$emit('change-name')
      }
    }
  }
</script>
<template>
  <h1>User: {{ user.name }}</h1>
  <p>Favorite Food: {{ user.favoriteFood }}</p>
  <button @click="tellParentChangeName">Change Name</button>
</template>
