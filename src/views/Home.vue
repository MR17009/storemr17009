<template>
  <v-container>
    <v-row>
      <!-- Filtros de la tienda -->
      <v-col lg="3" class="hidden-sm-and-down">
        <v-row>
          <v-col cols="12">
            <v-card color="red darken-3" dark>
              <v-row class="align-center">
                <v-col lg="3">
                  <v-switch v-model="switch1"></v-switch>
                </v-col>
                <v-col lg="4">
                  <label v-show="switch1 === false">Usados</label>
                  <label v-show="switch1 === true">Nuevos</label>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
        <!-- switch de nuevo -->

        <!-- marcas -->
        <v-row>
          <v-col lg="12">
            <v-card color="red darken-3" dark>
              <v-card-title>Marca</v-card-title>
              <v-card-text style="solid;">
                <v-checkbox
                  v-model="marcas"
                  value="Samsung"
                  :label="`Samsung`"
                ></v-checkbox>
                <v-checkbox
                  v-model="marcas"
                  value="Huawei"
                  :label="`Huawei`"
                ></v-checkbox>
                <v-checkbox
                  v-model="marcas"
                  value="Nokia"
                  :label="`Nokia`"
                ></v-checkbox>
                <v-checkbox
                  v-model="marcas"
                  value="¡Phone"
                  :label="`¡Phone`"
                ></v-checkbox>
                <v-checkbox
                  v-model="marcas"
                  value="Xiaomi"
                  :label="`Xiaomi`"
                ></v-checkbox>
                <v-checkbox
                  v-model="marcas"
                  value="Motorola"
                  :label="`Motorola`"
                ></v-checkbox>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>

        <!-- sistemas -->
        <v-row>
          <v-col lg="12">
            <v-card color="red darken-3" dark>
              <v-card-title>Sistema</v-card-title>
              <v-card-text>
                <v-checkbox
                  v-model="sistemas"
                  value="Android"
                  :label="`Android`"
                ></v-checkbox>
                <v-checkbox
                  v-model="sistemas"
                  value="Windows"
                  :label="`Windows`"
                ></v-checkbox>
                <v-checkbox
                  v-model="sistemas"
                  value="Ios"
                  :label="`Ios`"
                ></v-checkbox>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>

        <!-- pantallas -->
        <v-row>
          <v-col lg="12">
            <v-card color="red darken-3" dark>
              <v-card-title>Pantalla</v-card-title>
              <v-card-text>
                <v-checkbox
                  v-model="pantallas"
                  value="7.0"
                  :label="`7.0`"
                ></v-checkbox>
                <v-checkbox
                  v-model="pantallas"
                  value="6.5"
                  :label="`6.5`"
                ></v-checkbox>
                <v-checkbox
                  v-model="pantallas"
                  value="6.0"
                  :label="`6.0`"
                ></v-checkbox>
                <v-checkbox
                  v-model="pantallas"
                  value="5.5"
                  :label="`5.5`"
                ></v-checkbox>
                <v-checkbox
                  v-model="pantallas"
                  value="5.0"
                  :label="`5.0`"
                ></v-checkbox>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
      <v-col cols="12" sm="12" lg="9" md="9">
        <v-row>
          <!-- ordenar por -->
          <v-col lg="6" md="7" sm="7">
            <v-card class="pt-10" color="red darken-3" dark>
              <v-row>
                <v-col lg="6">
                  <v-row class="justify-center"
                    ><label>Ordenar Por:</label></v-row
                  >
                  <v-row class="justify-center">
                    <v-radio-group v-model="radioGroup">
                      <v-radio :label="`Asc`" :value="1"></v-radio>
                      <v-radio :label="`Des`" :value="2"></v-radio>
                    </v-radio-group>
                  </v-row>
                </v-col>
                <v-col lg="5">
                  <v-select
                    :items="items"
                    label="Opcion"
                    v-model="opcion"
                    outlined
                  ></v-select>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
          <v-navigation-drawer v-model="drawer" app absolute temporary>
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

          <!-- rango de precios -->
          <v-col
            lg="6"
            cols="12"
            md="6"
            sm="6"
            v-if="$vuetify.breakpoint.mdAndUp"
          >
            <v-card flat color="red darken-3" dark>
              <v-card-title class="justify-center"
                >Rango de precios ($)</v-card-title
              >
              <v-card-text>
                <v-row>
                  <v-col class="px-4">
                    <v-range-slider
                      v-model="range"
                      :max="max"
                      :min="min"
                      hide-details
                      class="align-center"
                      color="white"
                      background-color="red darken-3"
                    >
                      <template v-slot:prepend>
                        <v-text-field
                          :value="range[0]"
                          class="mt-0 pt-0"
                          hide-details
                          single-line
                          type="number"
                          style="width: 60px"
                          @change="$set(range, 0, $event)"
                        >
                        </v-text-field>
                      </template>
                      <template v-slot:append>
                        <v-text-field
                          :value="range[1]"
                          class="mt-0 pt-0"
                          hide-details
                          single-line
                          type="number"
                          style="width: 60px"
                          @change="$set(range, 1, $event)"
                        >
                        </v-text-field>
                      </template>
                    </v-range-slider>
                  </v-col>
                </v-row>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
        <v-row class="pt-10">
          <!-- productos de la pagina -->
          <v-col lg="3" v-for="(producto, key) in buscarProductos" :key="key">
            <div class="center">
            <v-card class="text-center">
              <v-img height="250px" :src="producto.imagenes[0]"> </v-img>
              <v-card-text class="text-truncate">
                <h2 class="black--text">${{ producto.precio }}</h2>
                <span>{{ producto.titulo }}</span>
              </v-card-text>
              <v-card-actions >
                <v-btn :to="'/anuncio/' + producto.id" text="red" color="error"
                  >Detalles</v-btn>
              </v-card-actions>
            </v-card>
            </div>
          </v-col>
        </v-row>
        <v-row>
          <!-- paginador -->
          <v-col lg="8">
            <div class="text-center">
              <v-pagination
                v-model="page"
                :length="tamanio"
                :total-visible="7"
                color="red"
                circle
              ></v-pagination>
            </div>
          </v-col>
          <v-col
            lg="4"
            class="text-center"
            style="
              display: flex;
              align-items: center;
              justify-content: center;
              gap: 15px;
              color: red;
            "
          >
            <span>Articulos por pagina</span>
            <v-select
              :items="articulos"
              v-model="e1"
              single-line
              color="red"
              style="max-width: 64px"
            >
            </v-select>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { db } from "../db";

export default {
  name: "Home",

  data() {
    return {
      // switch de nuevo producto
      switch1: false,

      // marcas de celulares
      marcas: [],

      // sistemas de los productos
      sistemas: [],

      // tamano de pantallas
      pantallas: [],

      // valores del rango de precio
      range: [0, 1000],
      min: 0,
      max: 1000,

      // valor de asc y des
      radioGroup: 0,

      // items de Ordenar por
      items: ["precio", "nombre"],

      opcion: "",

      // productos de la base de datos
      productos: [],

      // #pagina del pagination
      page: 1,

      // #articulos por pagina default
      e1: 3,

      // tamanio de paginador
      tamanio: 0,

      // articulos por pagina
      articulos: [3, 9, 12, 21, 27],
    };
  },

  methods: {
    tamPaginas(arreglo) {
      this.tamanio = 0;
      if (arreglo.length >= this.e1) {
        if (arreglo.length % this.e1 > 0) {
          this.tamanio = Math.trunc(arreglo.length / this.e1) + 1;
        } else {
          this.tamanio = arreglo.length / this.e1;
        }
      } else {
        this.tamanio = 1;
      }
    },

    paginarProductos(arreglo) {
      let nuevo = [];
      for (let i = (this.page - 1) * this.e1; i < this.page * this.e1; i++) {
        if (i < arreglo.length) {
          nuevo.push(arreglo[i]);
        }
      }
      return nuevo;
    },
  },
  props: ["busqueda"],
  computed: {
    // filtro por categorias y rango de precios
    selectedItems: function () {
      return this.productos.filter(function (newProductos) {
        if (
          this.marcas.length > 0 ||
          this.pantallas.length > 0 ||
          this.sistemas.length > 0
        ) {
          if ((this.marcas.length > 0) & (this.pantallas.length > 0)) {
            return (
              this.marcas.includes(newProductos.marca) &
              this.pantallas.includes(newProductos.pantalla) &
              (this.switch1 === newProductos.nuevo) &
              ((newProductos.precio >= this.range[0]) &
                (newProductos.precio <= this.range[1]))
            );
          } else if ((this.marcas.length > 0) & (this.sistemas.length > 0)) {
            return (
              this.marcas.includes(newProductos.marca) &
              this.sistemas.includes(newProductos.sistema) &
              (this.switch1 === newProductos.nuevo) &
              ((newProductos.precio >= this.range[0]) &
                (newProductos.precio <= this.range[1]))
            );
          } else if ((this.sistemas.length > 0) & (this.pantallas.length > 0)) {
            return (
              this.sistemas.includes(newProductos.sistema) &
              this.pantallas.includes(newProductos.pantalla) &
              (this.switch1 === newProductos.nuevo) &
              ((newProductos.precio >= this.range[0]) &
                (newProductos.precio <= this.range[1]))
            );
          } else {
            return (
              (this.marcas.includes(newProductos.marca) ||
                this.sistemas.includes(newProductos.sistema) ||
                this.pantallas.includes(newProductos.pantalla)) &
              (this.switch1 === newProductos.nuevo) &
              ((newProductos.precio >= this.range[0]) &
                (newProductos.precio <= this.range[1]))
            );
          }
        } else {
          return (
            !this.marcas.includes(newProductos.marca) &
            !this.sistemas.includes(newProductos.sistema) &
            !this.pantallas.includes(newProductos.pantalla) &
            (this.switch1 === newProductos.nuevo) &
            ((newProductos.precio >= this.range[0]) &
              (newProductos.precio <= this.range[1]))
          );
        }
      }, this);
    },

    // ordenar Productos
    orderarProductos: function () {
      let y = this.paginarProductos(this.selectedItems);
      let copia = y.slice();
      // precio Asc
      if (this.radioGroup === 1 && this.opcion === "precio") {
        return copia.sort((a, b) => {
          if (a.precio === b.precio) {
            return 0;
          }

          if (a.precio < b.precio) {
            return -1;
          }

          if (a.precio > b.precio) {
            return 1;
          }
        });
        // precio Des
      } else if (this.radioGroup === 2 && this.opcion === "precio") {
        return copia.sort((a, b) => {
          if (a.precio === b.precio) {
            return 0;
          }

          if (a.precio < b.precio) {
            return 1;
          }

          if (a.precio > b.precio) {
            return -1;
          }
        });
        // nombre Asc
      } else if (this.radioGroup === 1 && this.opcion === "nombre") {
        return copia.sort((a, b) => {
          if (a.titulo.toLowerCase() === b.titulo.toLowerCase()) {
            return 0;
          }

          if (a.titulo.toLowerCase() < b.titulo.toLowerCase()) {
            return -1;
          }

          if (a.titulo.toLowerCase() > b.titulo.toLowerCase()) {
            return 1;
          }
        });
        // nombre Des
      } else if (this.radioGroup === 2 && this.opcion === "nombre") {
        return copia.sort((a, b) => {
          if (a.titulo.toLowerCase() === b.titulo.toLowerCase()) {
            return 0;
          }

          if (a.titulo.toLowerCase() < b.titulo.toLowerCase()) {
            return 1;
          }

          if (a.titulo.toLowerCase() > b.titulo.toLowerCase()) {
            return -1;
          }
        });
        // fecha Asc
      } else if (this.radioGroup === 1 && this.opcion === "fecha") {
        return copia.sort((a, b) => {
          if (new Date(a.fecha) === new Date(b.fecha)) {
            return 0;
          }

          if (new Date(a.fecha) < new Date(b.fecha)) {
            return -1;
          }

          if (new Date(a.fecha) > new Date(b.fecha)) {
            return 1;
          }
        });
        // fecha Des
      } else if (this.radioGroup === 2 && this.opcion === "fecha") {
        return copia.sort((a, b) => {
          if (new Date(a.fecha) === new Date(b.fecha)) {
            return 0;
          }

          if (new Date(a.fecha) < new Date(b.fecha)) {
            return 1;
          }

          if (new Date(a.fecha) > new Date(b.fecha)) {
            return -1;
          }
        });
      } else {
        return copia;
      }
    },

    // buscar productos segun el titulo
    buscarProductos: function () {
      if (this.busqueda.length === 0) {
        this.tamPaginas(this.selectedItems.slice());
        return this.orderarProductos.slice();
      } else {
        let y = this.productos.filter((item) => {
          let x = item.titulo
            .toLowerCase()
            .indexOf(this.busqueda.toLowerCase());
          return x >= 0;
        });
        this.tamPaginas(y);
        let w = this.paginarProductos(y);
        return w;
      }
    },
  },

  firestore: {
    productos: db.collection("productos"),
  },
};
</script>

