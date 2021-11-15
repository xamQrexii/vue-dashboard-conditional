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
        <span class="text-sm text-gray-400 block">Welcome back</span>
        <h1 class="text-2xl font-bold">Login to your account</h1>
        <form
          class="mt-5"
          @submit="this.$emit('handleLogin', $event, email, password)"
        >
          <custom-input
            type="email"
            placeholder="Email"
            v-model="email"
            :required="true"
          ></custom-input>
          <custom-input
            type="password"
            placeholder="Password"
            v-model="password"
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
            Login
          </button>
        </form>
        <p class="text-sm font-normal mt-5">
          Don't have an account?
          <span
            class="
              text-sm text-blue-500
              cursor-pointer
              hover:text-blue-300
              transition-all
              duration-300
            "
            >Sign up now!</span
          >
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import CustomInput from "../components/CustomInput.vue";

export default {
  name: "Login",
  components: {
    CustomInput,
  },
  data() {
    return {
      email: "",
      password: "",
    };
  },
  emits: ["handleLogin"],
};
</script>

<style scoped>
.bg-img {
  background-image: url("../assets/images/login-page.jpg");
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
