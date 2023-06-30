<script>
export default {
  data: () => ({
    favoriteList: [],
  })
}
</script>

<template>
  <h1>Favorite List</h1>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(character,index) in favoriteList" :key="`odd-character-${index}`">{{ character }}</li>
  </ul>
  <p v-else>There are no Favorites</p>
</template>