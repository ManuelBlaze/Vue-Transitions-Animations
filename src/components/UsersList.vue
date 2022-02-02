<template>
  <ul>
    <li v-for="user in users" :key="user" @click="removeUser(user)">
      {{ user }}
    </li>
  </ul>
  <div>
    <input type="text" v-model.trim="name" />
    <button @click="addUser">Add User</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: ['Max', 'Manuel', 'Julie', 'Angela', 'Michael'],
      name: '',
    };
  },
  methods: {
    addUser() {
      if (!this.name) {
        return;
      }
      this.users.unshift(this.name);
      this.name = '';
    },
    removeUser(user) {
      this.users = this.users.filter((usr) => usr !== user);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

li {
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 15px;
  text-align: center;
  cursor: pointer;
}

button {
  margin-left: 10px;
}
</style>
