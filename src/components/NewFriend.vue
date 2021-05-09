<template>
  <h1>Add new friend</h1>
  <form @submit="onSubmit" @keyup.enter="onSubmit">
    <input type="text" placeholder="Name" v-model="name"/>
    <input type="text" placeholder="Phone" v-model="phone"/>
    <input type="text" placeholder="E-mail" v-model="email"/>
    <button type="submit">Add</button>
  </form>
</template>

<script>
export default {
  name: "NewFriend",
  data() {
    return {
      name: "",
      phone: "",
      email: "",
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      
        if (!this.name || !this.phone || !this.email) {
            alert ("All field is required!")
            return
        }

      const newFriend = {
          id: Math.floor(Math.random() *1000000),
          name: this.name,
          phone: this.phone,
          email: this.email,
          favorite: false
      }

      this.$emit("new-friend", newFriend)
      this.name = "";
      this.phone = "";
      this.email = "";
    },
  },
};
</script>

<style lang="scss" scoped>
h1 {
  text-align: center;
  color: #58004d;
}
form {
  text-align: center;
  input {
    display: block;
    margin: 10px auto;
  }
}
</style>
