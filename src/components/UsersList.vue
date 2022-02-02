<template>
  <transition-group tag="ul" name="user-list">
    <li v-for="user in users" :key="user" @click="removeUser(user)">
      {{ user }}
    </li>
  </transition-group>
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

.user-list-enter-from,
.user-list-leave-to {
  opacity: 0;
  transform: translateX(-30px);
}

.user-list-enter-active {
  transition: all 0.2s ease-out;
}

.user-list-leave-active {
  transition: all 0.15s ease-in;
}

.user-list-enter-to,
.user-list-leave-from {
  opacity: 1;
  transform: translateX(0);
}
</style>
