<template>
  <div>
    <myheader></myheader>
    <p v-if="msg.length > 0">{{msg}}</p>
    <p v-else>no text</p>
    <input type="text" v-model="msg" />
    <button @click="clear()">clear</button>
    <ul>
      <li v-for="(user, key) in users" :key="key">{{ user.name }}</li>
    </ul>
  </div>
</template>

<script>
import myheader from "./components/myheader";
import axios from "axios";

export default {
  components: {
    myheader
  },
  data() {
    return {
      msg: "Hello World",
      users: []
    };
  },
  methods: {
    clear() {
      this.msg = "";
    }
  },
  mounted: function() {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then(response => (this.users = response.data));
  }
};
</script>
