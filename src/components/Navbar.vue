<template>
  <v-container>
    <v-app-bar app color="red darken-4" dark>
      <!-- boton del sidenav -->
      <v-app-bar-nav-icon
        class="hidden-md-and-up"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <!-- logo de la tienda -->
      <v-toolbar-title>
        <v-btn
          plain
          class="white--text hidden-sm-and-down"
          style="text-decoration: none"
          :to="'/'"
          ><v-icon large>mdi-store</v-icon>CellPhone Store</v-btn
        >
      </v-toolbar-title>

      <v-text-field
        label="Buscar"
        v-model="cadena"
        solo-inverted
        hide-details
        class="pl-10 pr-10 ml-4"
        @keyup.capture="buscar"
      >
        <v-icon
          slot="append"
          color="black"
          @click="borrar"
          v-show="cadena.length > 0"
          >mdi-close</v-icon
        >
      </v-text-field>
      <v-spacer class="hidden-sm-and-down"></v-spacer>

      <v-btn plain class="hidden-sm-and-down" :to="'/'">Inicio</v-btn>
      <v-btn plain class="hidden-sm-and-down" :to="'/'">Estadisticas</v-btn>
      <v-btn icon class="hidden-sm-and-down" @click="openModal"
        ><v-icon large>mdi-plus</v-icon></v-btn
      >
      <v-btn class="hidden-sm-and-down" icon @click="openCarrito"
        ><v-icon large>mdi-cart</v-icon></v-btn
      >
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" app absolute temporary right>
      <v-list>
        <v-list-item>
          <v-list-item-icon>
            <v-icon>mdi-store</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-btn plain :to="'/'"><b>CellPhone Store</b></v-btn>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item>
          <v-list-item-content>
            <v-btn plain :to="'/'">Inicio</v-btn>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-content>
            <v-btn plain @click="openModal">Nuevo Anuncio</v-btn>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-content>
            <v-btn plain @click="openCarrito">Carrito</v-btn>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-content>
            <v-btn plain :to="'/'">Estadisticas</v-btn>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <Modal ref="modal" @guardado="mensaje = $event"> </Modal>
    <Carrito ref="carrito"></Carrito>

    <!-- mensaje de producto guardado -->
    <v-snackbar v-model="mensaje" :timeout="2000">
      {{ texto }}

      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="closeMensaje()">
          Cerrar
        </v-btn>
      </template>
    </v-snackbar>
  </v-container>
</template>

<script>
import Modal from "./Modal.vue";
import Carrito from "./Carrito.vue";

export default {
  data() {
    return {
      // cadena de busqueda
      cadena: "",
      texto: "Se ha guardado el producto",
      mensaje: false,
      drawer: false,
    };
  },
  components: { Modal, Carrito },

  methods: {
    // abrimos el modal
    openModal() {
      this.$refs.modal.dialog = true;
      // se formatea el snackbar
      this.mensaje = false;
      this.$refs.modal.snackbar = false;
    },

    openCarrito() {
      this.$refs.carrito.dialog = true;
      // se formatea el snackbar
      // this.mensaje = false;
      // this.$refs.modal.snackbar = false;
    },

    // mando el valor de la cadena al App.vue
    buscar() {
      this.$emit("busqueda", this.cadena);
    },

    // borramos la cadena
    borrar() {
      this.cadena = "";
    },

    // se cierra el mensaje al dar CLOSE
    closeMensaje() {
      this.$refs.modal.snackbar = false;
    },
  },
};
</script>

<style>
</style>