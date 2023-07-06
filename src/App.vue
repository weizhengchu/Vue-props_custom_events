<template>
  <section>
    <header>
      <h1>Users</h1>
    </header>
    <user-data @add-contact="addContact"></user-data>
    <ul>
      <active-user
        v-for="user in users"
        :key="user.id"
        :id="user.id"
        :name="user.name"
        :age="user.age"
        :is-favorite="user.isFavorite"
        @toggle-favorite="toggleFavoriteStatus"
        @delete="deleteContact"
      ></active-user>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      users: [],
    };
  },
  methods: {
    toggleFavoriteStatus(userId) {
      console.log("is working");
      const identifiedFriend = this.users.find((user) => user.id === userId);
      identifiedFriend.isFavorite = !identifiedFriend.isFavorite;
    },
    addContact(name, age) {
      const newFriendContact = {
        id: new Date().toISOString(),
        name: name,
        age: age,
        isFavorite: false,
      };
      this.users.push(newFriendContact);
    },
    deleteContact(userId) {
      this.users = this.users.filter((user) => user.id !== userId);
    },
  },
};
</script>
