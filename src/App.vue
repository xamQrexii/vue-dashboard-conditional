<template>
  <login
    v-if="currentView === 'login' && !isLoggedIn"
    @handle-login="handleLogin"
    @change-view="changeView"
  ></login>
  <register
    v-else-if="currentView === 'register' && !isLoggedIn"
    @handle-register="handleRegister"
    @change-view="changeView"
  ></register>
  <dashboard
    v-else-if="currentView === 'dashboard' && isLoggedIn"
    :users="users"
    :current-user="currentUser"
    @logout="logout"
    @set-current-user="setCurrentUser"
  ></dashboard>
</template>

<script>
import Login from "./views/Login.vue";
import Register from "./views/Register.vue";
import Dashboard from "./views/Dashboard.vue";

export default {
  name: "App",
  components: {
    Login,
    Register,
    Dashboard,
  },
  data() {
    return {
      isLoggedIn: false,
      users: [
        {
          id: "001",
          firstName: "muhammad",
          lastName: "osama",
          email: "muosama@nisum.com",
          password: "123456",
        },
        {
          id: "002",
          firstName: "muhammad",
          lastName: "ismail",
          email: "ismail@xyz.com",
          password: "123456",
        },
        {
          id: "003",
          firstName: "ahsan",
          lastName: "tariq",
          email: "ahsan@xyz.com",
          password: "123456",
        },
      ],
      currentUser: null,
      currentView: "login",
    };
  },
  methods: {
    changeView(name) {
      this.currentView = name;
    },
    setCurrentUser(user) {
      this.currentUser = user;
    },
    findUser({ email }) {
      return this.users.find((user) => user.email === email);
    },
    logout() {
      console.log("logout is working");
      this.isLoggedIn = false;
      this.changeView("login");
      this.currentUser = null;
    },
    handleLogin(user) {
      const foundUser = this.findUser(user);

      if (foundUser && foundUser.password === user.password) {
        this.isLoggedIn = true;
        this.changeView("dashboard");
      } else {
        alert("Please provide valid email and password");
      }
    },
    handleRegister(user) {
      const isUserExist = this.findUser(user);

      if (isUserExist) {
        alert("Email already exist");
      }

      if (!isUserExist) {
        this.users.push(user);
        alert("User registerd successfully");
        return true;
      }
    },
  },
};
</script>

<style scoped></style>
