<template>
  <div class="home px-44 py-32">
    <h1 class="text-gray-600 font-bold text-2xl text-center">Register</h1>
    <form
      class="border-2 border-gray-200 rounded-2xl px-12 py-16 mt-8 shadow-md"
      @submit.prevent="register()"
    >
      <div class="mb-6">
        <label
          class="
            block
            mb-2
            text-sm
            font-medium
            text-gray-900
            dark:text-gray-300
          "
          >Email</label
        >
        <input
          type="email"
          id="email"
          v-model="email"
          class="
            bg-gray-50
            border border-gray-300
            text-gray-900 text-sm
            rounded-lg
            focus:ring-blue-500 focus:border-blue-500
            block
            w-full
            p-2.5
            dark:bg-gray-700
            dark:border-gray-600
            dark:placeholder-gray-400
            dark:text-white
            dark:focus:ring-blue-500
            dark:focus:border-blue-500
          "
          placeholder="Masukan Email"
          required
        />
      </div>
      <div class="mb-6">
        <label
          class="
            block
            mb-2
            text-sm
            font-medium
            text-gray-900
            dark:text-gray-300
          "
          >Username</label
        >
        <input
          type="username"
          id="username"
          v-model="username"
          class="
            bg-gray-50
            border border-gray-300
            text-gray-900 text-sm
            rounded-lg
            focus:ring-blue-500 focus:border-blue-500
            block
            w-full
            p-2.5
            dark:bg-gray-700
            dark:border-gray-600
            dark:placeholder-gray-400
            dark:text-white
            dark:focus:ring-blue-500
            dark:focus:border-blue-500
          "
          placeholder="Masukan Username"
          required
        />
      </div>
      <div class="mb-6">
        <label
          for="password"
          class="
            block
            mb-2
            text-sm
            font-medium
            text-gray-900
            dark:text-gray-300
          "
          >Password</label
        >
        <input
          type="password"
          id="password"
          v-model="password"
          class="
            bg-gray-50
            border border-gray-300
            text-gray-900 text-sm
            rounded-lg
            focus:ring-blue-500 focus:border-blue-500
            block
            w-full
            p-2.5
            dark:bg-gray-700
            dark:border-gray-600
            dark:placeholder-gray-400
            dark:text-white
            dark:focus:ring-blue-500
            dark:focus:border-blue-500
          "
          required
        />
      </div>

      <button
        type="submit"
        class="
          text-white
          bg-blue-700
          hover:bg-blue-800
          focus:ring-4 focus:outline-none focus:ring-blue-300
          font-medium
          rounded-lg
          text-sm
          w-full
          sm:w-auto
          px-5
          py-2.5
          text-center
          dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800
        "
      >
        Submit
      </button>
      <br />
    </form>
    <router-link to="/" class="underline my-9 text-center text-blue-600"
      >Login</router-link
    >
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Register",
  data() {
    return {
      username: "",
      password: "",
      email: "",
    };
  },
  methods: {
    async register() {
      const auth = {
        username: this.username,
        password: this.password,
        email: this.email,
      };
      try {
        await axios
          .post("http://94.74.86.174:8080/api/register", auth)
          .then((res) => res.data, this.$router.push("/checklist"));
        alert("sukses Register");
      } catch (err) {
        this.$router.push("/");
        alert("gagal Register");
        this.error = err.message;
        console.log(this.auth);
      }
    },
  },
};
</script>
