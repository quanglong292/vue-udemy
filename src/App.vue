<template>
  <section>
    <header>
      <h1>My Friends {{ friends[0].name }}</h1>
    </header>

    <ul>
      <FriendContact
        v-for="item in friends"
        :key="item.id"
        :id="item.id"
        :name="item.name"
        :phone-number="item.phone"
        :email-address="item.email"
        :isFavorite="item.favorite"
        @toggle-favorite="toggleFavorite"
      />
    </ul>
  </section>
</template>

<script>
import FriendContact from "./components/FriendContact";

export default {
  components: {
    FriendContact,
  },
  data: () => ({
    friends: [
      {
        id: "manuel",
        name: "Manuel",
        phone: "123",
        email: "manuel123@gmail.com",
        favorite: true
      },
      {
        id: "ozil",
        name: "Ozil",
        phone: "12345",
        email: "ozil1235@gmail.com",
        favorite: false
      },
      {
        id: "messi",
        name: "Messi",
        phone: "354534",
        email: "messi123543@gmail.com",
        favorite: true
      },
    ],
  }),
  methods: {
    toggleFavorite (id) {
      const index = this.friends.findIndex(item => item.id === id)
      console.log(this.friends[index].favorite)
      this.friends[index].favorite = !this.friends[index].favorite
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: "Jost", sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>
