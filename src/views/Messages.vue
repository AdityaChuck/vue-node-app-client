<template>
  <v-card>
    <v-toolbar :dark="true" >
      <v-toolbar-title>MESSAGES</v-toolbar-title>
    </v-toolbar>
    <v-row class="mb-6">
      <v-col cols="3" />
      <v-col cols="6">
        <v-list>
          <v-list-item
            v-for="(item, i) in messages"
            :key="i"
            @click="nothing"
          >
            <v-list-item-content>
              <v-list-item-title v-text="item.body"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-col>
      <v-col cols="3" />
    </v-row>
  </v-card>
</template>

<script>
import axios from "axios";

export default {
  name: "Messages",
  data: () => ({
    messages: [],
  }),
  mounted: async function() {
    const response = await axios.get("http://192.168.43.147:3000/messages");
    this.messages = response.data.data;
  },
  methods: {
    nothing: function(i) {
      console.log(i);
      return;
    },
  },
};
</script>
