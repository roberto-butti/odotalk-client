<template>
  <v-card width="400" class="mx-auto mt-5">
    <v-card-title class="pb-0">
      <h2>Login</h2>
    </v-card-title>
    <v-card-text>
      <v-form @submit.prevent="sendCredential">
        <v-text-field v-model="username" label="Username" prepend-icon="mdi-account" />
        <v-text-field
          v-model="password"
          :type="showPassword ? 'text' : 'password'"
          label="Password"
          prepend-icon="mdi-lock-outline"
          :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="showPassword = !showPassword"
        />
      </v-form>
    </v-card-text>
    <v-divider></v-divider>
    <v-card-actions>
      <v-btn color="success">Register</v-btn>
      <v-spacer></v-spacer>
      <v-btn @click="sendCredential" color="info">Login</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
//import { axios } from "axios";
const axios = require("axios");
export default {
  data: () => ({
    showPassword: false,
    username: "",
    password: "",
    submitted: false
  }),
  methods: {
    sendCredential(e) {
      console.log(e);
      console.log(this.username);
      console.log(this.password);
      console.log(axios);
      axios
        .post(process.env.VUE_APP_HOST_API + "/oauth/token", {
          username: this.username,
          password: this.password,
          grant_type: "password",
          client_id: process.env.VUE_APP_CLIENT_ID,
          client_secret: process.env.VUE_APP_CLIENT_SECRET
        })
        .then(function(response) {
          console.log(response.data);
          //currentObj.output = response.data;
        })
        .catch(function(error) {
          //currentObj.output = error;
          console.log(error);
        });
    }
  }
};
</script>