<script>
  export default {
    data: () => ({
      characterList: [
      {
        name: "Aang",
        element: ["Air", "Water", "Fire", "Earth", "Iron"]
      },
      {
        name: "Zuko",
        element: ["Water"]
      },
      {
        name: "Toph",
        element: ["Earth"]
      },
      {
        name: "Katara",
        element: ["Water"]
      }
    ],
    favoriteList: []
    }),

    methods: {
      addToFav(character) {
        this.favoriteList.push(character)
      }
    }
  }
</script>

<template>
  <h2>Characters</h2>
  <p v-if="characterList.length === 0">There are no characters</p>
  <ul v-else-if="characterList.length % 2 === 0">
    <li v-for="(character,index) in characterList" :key="`even-character-${index}`">
      <p>{{ character.name }}</p>
      <button @click="addToFav(character)">⭐Favorite</button>
    </li>
  </ul>
  <p v-else>There are odd characters!</p>
</template>