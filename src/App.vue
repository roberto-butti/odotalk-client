<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>ODO</span>
        <span class="font-weight-light">talk</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text href="https://github.com/vuetifyjs/vuetify/releases/latest" target="_blank">
        <span class="mr-2">Latest Release</span>
      </v-btn>
    </v-app-bar>

    <v-content>
      <Login />
    </v-content>
  </v-app>
</template>

<script>
//import HelloWorld from "./components/HelloWorld";
import Login from "./components/Login";

export default {
  name: "App",
  components: {
    //HelloWorld,
    Login
  },
  data: () => ({
    //
  })
};
</script>
