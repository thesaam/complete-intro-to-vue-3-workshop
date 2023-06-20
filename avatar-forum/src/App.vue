<script>
import BenderStatistics from './components/BenderStatistics.vue';

export default {
  components: {
    BenderStatistics
  },

  data: () => ({
    newCharacter: {
      name: "",
      element: []
    },
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
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
      this.newCharacter = { name: ""}
      console.log(this.newCharacter);
    },
    addToFav(character) {
      this.favoriteList.push(character)
    }
  }
}
</script>

<template>
  <BenderStatistics :characters="characterList" />

  <h2>Characters</h2>
  <p v-if="characterList.length === 0">There are no characters</p>
  <ul v-else-if="characterList.length % 2 === 0">
    <li v-for="(character,index) in characterList" :key="`even-character-${index}`">
      <p>{{ character.name }}</p>
      <button @click="addToFav(character)">⭐Favorite</button>
    </li>
  </ul>
  <p v-else>There are odd characters!</p>
  <h1>Favorite List</h1>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(character,index) in favoriteList" :key="`odd-character-${index}`">{{ character }}</li>
  </ul>
  <p v-else>There are no Favorites</p>
  <h2>New character</h2>
  <pre>{{ newCharacter }}</pre>
  <label for="name">Name</label>
  <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter">
  <p>
    <span v-for="(character,index) in characterList" :key="`comma-list-character-${index}`">
      {{ character.name }}
      {{ index === characterList.length - 1 ? " " : ", "}}
    </span>
  </p>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
