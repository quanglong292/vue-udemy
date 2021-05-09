<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? "(Favorite)" : "" }}</h2>
    <button @click="toggleDetail">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone: </strong>{{ phoneNumber }}</li>
      <li><strong>Email: </strong>{{ emailAddress }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  name: "FriendContact",
  // props: ["name", "phoneNumber", "emailAddress", "isFavorite"],
  props: {
    name: String,
    phoneNumber: String,
    emailAddress: String,
    isFavorite: Boolean,
    id: String,
  },
  data() {
    return { detailsAreVisible: false};
  },
  methods: {
    toggleDetail() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
     this.$emit('toggle-favorite', this.id)
    },
  },
};
</script>
