<template>
  <v-row>
    <v-dialog
      v-model="dialog"
      fullscreen
      hide-overlay
    >
      <v-card style="background-color: white">
        <v-toolbar dark color="red darken-3">
          <v-btn icon dark @click="cancelar()">
            <v-icon>mdi-close</v-icon>
          </v-btn>
          <v-toolbar-title>Carrito</v-toolbar-title>
          <v-spacer></v-spacer>
        </v-toolbar>

        <v-container class="pt-12"> </v-container>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
export default {
  name: "Carrito",
  data() {
    return {
      dialog: false,
    };
  },
  methods: {
    cancelar() {
      this.dialog = false;
    },
  },
};
</script>

<style>
</style>