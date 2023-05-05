<template>
  <div>
    <p v-for="manu in manufacturer" :key="manu.id">
      {{ manu.id }}-{{ manu.Title }}
    </p>
    <input placeholder="id" v-model="id" />
    <input placeholder="id" v-model="Title" />
    <button @click="post()">Post</button>
    <button @click="put()">Put</button>
    <button @click="remove()">Delete</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      text: "test",
      manufacturer: [{ id: 2, Title: "P" }],
      id: "",
      Title: "",
    };
  },
  created() {
    this.get();
  },
  methods: {
    get() {
      axios.get("https://localhost:7085/api/manufacturers").then((respone) => {
        this.manufacturer = respone.data;
      });
    },
  },
};
</script>