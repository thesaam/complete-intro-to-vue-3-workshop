<script>
import UserCard from './components/UserCard.vue'
import BaseCounter from './components/BaseCounter.vue'
 export default {
  components: {
    BaseCounter,
    UserCard
  },

  data() {
    return {
      count: 0,
      counterTitle: "Counter Standard",
      incrementAmount: 10,
      message: 'Hello it works!',
      listOfNumbers: [
        { 
          name: 1, 
          id: 'f796050d-b492-4cef-a472-f38606221779', 
          list: [ 1, 2, 3]
        }, 
        { 
          name: 2, 
          id: '0a6c07e3-3f1d-4347-985b-125ba195585c',
          list: [ 1, 2, 3]
        }, 
        { 
          name: 3, 
          id: '7778db6a-ecf9-4f11-a946-9db53743d3a4', 
          list: [ 1, 2, 3]
        }, 
        { 
          name: 4, 
          id: '28af535b-fd8f-4b09-a404-c5a96e96c470', 
          list: [ 1, 2, 3]
        }, 
        { name: 5, 
          id: '89c28ef9-036a-4e5d-8cc9-39ca026f3932', 
          list: [ 1, 2, 3]
        }
      ],
      userData: {
        name: "Client",
        preferredFramework: "vue",
        favoriteFood: "Swallows",
        favoriteNumbers: [8,12,10]
      }
    };
  },
  

  watch: {
    count(newValue) {
      if(newValue > 20) {
        this.counterTitle += " Very Long"
      }
    }
  },

  computed: {
    refinedUserData() {
      return {
        name: this.userData.name,
        food: this.userData.favoriteFood
      }
    }
  }
};
</script>

<template>
  <UserCard :user="refinedUserData" />
  <BaseCounter />
  <hr/>
  <p v-if="message.length % 2 === 0">
    Even: {{ message }}
  </p>
  <p v-else>Odd: {{ message.toUpperCase() }}</p>
  <ul v-for="(item, index) in listOfNumbers" :key="`item.${index}`">
    <li>
      {{ item.id }}
      <ul>
        <li v-for="(number, index) in item.list" :key="`number-${index}`">
          {{ number }}
        </li>
      </ul>
    </li>
  </ul>
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
