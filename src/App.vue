<template>
  <div>
    <h1>Friend List</h1>
    <form action="">
      <table>
        <tr>
          <td>Name:</td>
          <td><input type="text" v-model="friend.name" /></td>
        </tr>
        <tr>
          <td>Phone:</td>
          <td><input type="text" v-model="friend.phone" /></td>
        </tr>
        <tr>
          <td>E-mail:</td>
          <td><input type="text" v-model="friend.email" /></td>
        </tr>
        <tr>
          <td><button type="submit" @click="sendData">Send</button></td>
          <td><button type="reset" @click="clearData">Clear</button></td>
        </tr>
      </table>
    </form>

    <h3>{{ friend }}</h3>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      friend: {
        name: "",
        phone: "",
        email: "",
      },
    };
  },
  methods: {
    sendData(e) {
      e.preventDefault();
      console.log("Active");

      axios
        .post("http://localhost/VueAPI/api.php", {
          name: this.friend.name,
          phone: this.friend.phone,
          email: this.friend.email,
        })
        .then(function(response) {
          console.log(response);
        })
        .catch(function(error) {
          console.log(error);
        });
      this.clearData();
    },

    clearData() {
      this.friend.name = "";
      this.friend.phone = "";
      this.friend.email = "";
    },
  },
};
</script>
