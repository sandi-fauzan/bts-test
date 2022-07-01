<template>
  <h2>Checklist</h2>
  <input type="text" @keyup.enter="getCheck()" v-model="checklist" />
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      checklist: [],
      items: [],
      user: "",
    };
  },
  methods: {
    // authHeader() {
    //   const authHeader = opts.headers["Authorization"];
    //   if (user && user.accessToken) {
    //     return { Authorization: "Bearer " + user.accessToken };
    //   } else {
    //     return {};
    //   }
    // },

    // async getCheck() {
    //   await axios.create({
    //     baseURL: "http://94.74.86.174:8080/api/checklist",
    //     headers: {
    //       Authorization: "Bearer :" + localStorage.getItem("Authorization"),
    //       "Content-type": "application/json",
    //     },
    //   });
    // },
    async getAllChecklist() {
      try {
        await axios
          .get("http://94.74.86.174:8080/api/checklist", this.auth)
          .then((res) => res.data, this.$router.push("/checklist"));
        alert("checklist diperbaharui");
      } catch (err) {
        this.$router.push("/");
        this.error = err.message;
      }
    },

    async createChecklist() {
      const res = await axios.post("http://94.74.86.174:8080/api/checklist", {
        body: this.checklist,
      });
      this.items = [...this.items, res.data];
      this.checklist = "";
      console.log(this.res.data);
    },
  },
  mounted() {
    this.getCheck();
  },
};
</script>