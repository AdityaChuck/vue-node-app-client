<template>
  <!-- <v-app>
    <v-app-bar app color="primary" dark>
      <router-link to="/" style="color:white;">Messages</router-link>

      <router-link to="/newMessage" style="color:white;">New Message</router-link>
    </v-app-bar>
    <v-main>
      <router-view />
    </v-main>
    
  </v-app> -->

  <div>
    
    <v-toolbar :dark="true" >
    <v-toolbar-title>
      <router-link to="/" style="color:white;">Messages</router-link>
    </v-toolbar-title>
    <v-spacer/>
    <v-toolbar-title>
       <router-link to="/newMessage" style="color:white;">New Message</router-link>
    </v-toolbar-title>
    <v-spacer></v-spacer>
  </v-toolbar>
  <br/>
  <v-container>
  <router-view />
  </v-container>
  </div>

</template>

<script>
export default {
  name: "App",
};
</script>
