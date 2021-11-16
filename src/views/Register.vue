<template>
  <!-- container -->
  <div class="flex min-h-screen">
    <!-- bg image -->
    <div class="bg-img flex-1 flex justify-center items-center">
      <div>
        <p class="text-yellow-500 text-7xl">DASHBOARD</p>
        <p class="text-white text-sm text-right">Conditional Rendering</p>
      </div>
    </div>
    <!-- form -->
    <div class="flex flex-1 justify-center items-center bg-gray-200">
      <div class="bg-white shadow-2xl rounded p-5 w-1/2">
        <span class="text-sm text-gray-400 block">Keep doing</span>
        <h1 class="text-2xl font-bold">Register your account</h1>
        <form class="mt-5" @submit="submit">
          <custom-input
            type="text"
            placeholder="First name"
            v-model.trim="user.firstName"
            :required="true"
          ></custom-input>
          <custom-input
            type="text"
            placeholder="Last name"
            v-model.trim="user.lastName"
            :required="true"
          ></custom-input>
          <custom-input
            type="email"
            placeholder="Email"
            v-model.trim="user.email"
            :required="true"
          ></custom-input>
          <custom-input
            type="password"
            placeholder="Password"
            v-model.trim="user.password"
            :required="true"
          ></custom-input>
          <button
            type="submit"
            class="
              mt-5
              mb-3
              w-full
              bg-green-500
              hover:bg-green-400
              text-white
              py-2
              rounded-md
              transition
              duration-300
            "
          >
            Register
          </button>
        </form>
        <p class="text-sm font-normal mt-5">
          Go to
          <span
            class="
              text-sm text-blue-500
              cursor-pointer
              hover:text-blue-300
              transition-all
              duration-300
            "
            @click="this.$emit('changeView', 'login')"
            >Login page!</span
          >
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import CustomInput from "../components/CustomInput.vue";

export default {
  name: "Register",
  components: {
    CustomInput,
  },
  data() {
    return {
      user: {
        firstName: "",
        lastName: "",
        email: "",
        password: "",
      },
    };
  },

  methods: {
    submit(e) {
      e.preventDefault();
      this.$emit("handleRegister", this.user);
      this.user = { firstName: "", lastName: "", email: "", password: "" };
    },
  },

  emits: ["handleRegister", "changeView"],
};
</script>

<style>
.bg-img {
  background-image: url("../assets/images/register-page.jpg");
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
