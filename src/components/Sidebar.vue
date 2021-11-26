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
    </v-row>
  </v-container>
</template>
<script>
export default {};
</script>