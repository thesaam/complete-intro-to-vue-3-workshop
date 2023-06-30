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
    }
  }
</script>
<template>
  <h1>User: {{ user.name }}</h1>
  <p>Favorite Food: {{ user.favoriteFood }}</p>
</template>
