<template>
  <v-app id="inspire" class="overflow-hidden">
    <!-- Top Nav Bar -->
    <v-app-bar app color="red" dark class="pl-2">
      <v-icon large>mdi-hospital</v-icon>
      <v-toolbar-title class="font-weight-black">NHIYA</v-toolbar-title>
      <v-spacer />

      <v-tooltip bottom>
        <template v-slot:activator="{ on }">
          <v-btn icon  dark v-on="on" @click="about = !about">
            <v-icon large> mdi-information</v-icon>
          </v-btn>
        </template>
        <span>Learn more about the app!</span>
      </v-tooltip>

      <v-dialog v-model="about" width="500" scrollable>
        <v-card>
          <v-card-title class="headline grey lighten-2" primary-title>About MyPermit!</v-card-title>

          <v-card-text class="pt-2">
            <h3>Do you want to find your permit or other permits quickly?</h3>
            <br />
            <p
              style="font-size:110%;"
            >Worry not because with MyPermit!, you can easily search for permits within any date range and find them on the map.</p>
            <br />
            <h3 style="text-align:center;">Thank You for Using MyPermit!</h3>
          </v-card-text>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn @click="about = false" icon>
              <v-icon>mdi-close</v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-app-bar>
    <!-- Leaflet Map -->
    <v-content>
      <v-container class="fill-height pa-0 ma-0" fluid>
        <mymap />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import mymap from "./leaflet";
//import axios from "axios";
//import { eventBus } from "../main.js";

export default {
  name: "toolbar",
  components: {
    mymap
  },
  props: {
    source: String
  },
  data: () => ({
    sheet: false,
    alert: "If you are seeing this, contact the developer",
    about: false
  }),

  methods: {
  }
};
</script>


<style scoped>
.date-range {
  padding-left: 30%;
  padding-right: 30%;
}

.sheets {
  opacity: 0.6;
}

.sheets:hover {
  opacity: 1;
}

.tool {
  z-index: 1000;
}
</style>