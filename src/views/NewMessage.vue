<template>
  <div>
    <v-card>
      <v-toolbar :dark="true">
        <v-toolbar-title>SEND A MESSAGE</v-toolbar-title>
      </v-toolbar>
      <br/>
      <v-row>
        <v-col cols="3" />
        <v-col cols="6">
          <form @submit.prevent="submit">
            <v-text-field
              v-model="msg.body"
              placeholder="Type message here"
              outlined
              required
            ></v-text-field>
            <v-btn :disabled="disabled" type="submit" block :dark="true"
              >submit</v-btn
            >
            <br/>
          </form>
        </v-col>
        <v-col cols="3" />
      </v-row>
    </v-card>
    <v-snackbar v-model="snackbar">
      {{ text }}

      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "NewMessage",
  data: () => ({
    msg: {
      body: "",
    },
    snackbar: false,
    text: "Message sent",
  }),
  computed: {
    disabled: function() {
      if (this.msg.body.length === 0) {
        return true;
      } else {
        return false;
      }
    },
  },
  methods: {
    submit: async function() {
      try {
        const res = await axios.post(
          "http://192.168.43.147:3000/messages",
          this.msg
        );
        if (res) {
          this.msg.body = "";
          this.snackbar = true;
        }
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>
