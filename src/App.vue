<template>
  <login
    v-if="currentView === 'login' && !isLoggedIn"
    @handle-login="handleLogin"
  ></login>
</template>

<script>
import Login from "./views/Login.vue";

export default {
  name: "App",
  components: {
    Login,
  },
  data() {
    return {
      isLoggedIn: false,
      users: [],
      currentUser: null,
      currentView: "login",
    };
  },
  methods: {
    handleLogin(e, email, password) {
      e.preventDefault();
      if (!email || !password) {
        alert("please provide username and password");
      }
    },
  },
};
</script>

<style scoped></style>
