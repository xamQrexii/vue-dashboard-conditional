<template>
  <div class="flex justify-center">
    <div class="w-1/2 p-5">
      <div class="flex justify-between">
        <p class="text-2xl font-bold">Dashboard</p>
        <button
          class="p-2 bg-yellow-500 hover:bg-yellow-300 text-white rounded"
          @click="this.$emit('logout')"
        >
          Logout
        </button>
      </div>
      <div v-if="currentUser">
        <h1>
          Selected user: {{ capitalizeName(currentUser.firstName) }}
          {{ capitalizeName(currentUser.lastName) }}
        </h1>
      </div>
      <table class="min-w-max w-full table-auto mt-5">
        <thead>
          <tr
            class="bg-gray-200 text-gray-600 uppercase text-sm leading-normal"
          >
            <th class="py-3 px-6 text-left">ID</th>
            <th class="py-3 px-6 text-left">FIRST NAME</th>
            <th class="py-3 px-6 text-center">LAST NAME</th>
            <th class="py-3 px-6 text-center">EMAIL</th>
            <th class="py-3 px-6 text-center">ACTION</th>
          </tr>
        </thead>
        <tbody class="text-gray-600 text-sm font-light">
          <tr
            class="border-b border-gray-200 hover:bg-gray-100"
            v-for="user in users"
            :key="user.id"
          >
            <td class="py-3 px-6 text-left whitespace-nowrap">
              {{ user.id }}
            </td>
            <td class="py-3 px-6 text-left whitespace-nowrap">
              {{ capitalizeName(user.firstName) }}
            </td>
            <td class="py-3 px-6 text-left whitespace-nowrap">
              {{ capitalizeName(user.lastName) }}
            </td>
            <td class="py-3 px-6 text-left whitespace-nowrap">
              {{ user.email }}
            </td>
            <td class="py-3 px-6 text-left whitespace-nowrap">
              <button
                class="p-2 bg-green-500 hover:bg-green-300 text-white rounded"
                @click="this.$emit('setCurrentUser', user)"
              >
                Show user
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dashbboard",
  props: ["users", "currentUser"],
  emits: ["setCurrentUser", "logout"],
  methods: {
    capitalizeName(value) {
      return value.charAt(0).toUpperCase() + value.slice(1);
    },
  },
};
</script>

<style></style>
