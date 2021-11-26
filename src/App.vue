<template>
  <v-app style="background-color: white">
    <NavBar @busqueda="newCad = $event" />
    <v-main>
      <router-view :busqueda="newCad" />
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import NavBar from "./components/Navbar.vue";
import { bus } from "./main";
import Footer from './components/Footer.vue';
export default {
  name: "App",
  components: {
    NavBar,
    Footer,
  },
  data() {
    //
    return {
      newCad: "",
      compras: [],
    };
  },

  methods: {
    mandarCompras() {
      bus.$emit("showCarrito", this.compras[this.compras.length - 1]);
      console.log("Si funciona ");
    },
  },

  created() {
    bus.$on("addCarrito", (data) => {
      this.compras.push(data);
      this.mandarCompras();
    });
  },
};
</script>