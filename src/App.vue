<template>
  <v-app>

    <v-app-bar app>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Crud tareas</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn class="mr-2 success">
        Ingresar
      </v-btn>
      <v-btn class=" error">
        Salir
      </v-btn>

     
    </v-app-bar>

    <v-navigation-drawer app v-model="drawer">
      <v-row class="mt-5 ml-3">
        <v-col>
          <v-avatar>
            <img
              src="data:image/png;base64,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">
          </v-avatar>
        </v-col>
      </v-row>

      <v-row class="ml-3">
          <v-col>
          <p class="headline mt-5">Nombre de Usuario</p>
        </v-col>
      </v-row>
      <v-row >
        <v-col>
          <v-btn class="success mb-2" block :to="{name: 'Home'}">Home</v-btn>
          <v-btn class="success" block :to="{name: 'Tareas-crud'}">Lista de Tareas</v-btn>
        </v-col>
      </v-row>
    </v-navigation-drawer>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    name: 'App',

    data() {
      return {
        drawer: false
      }
    }
  };
</script>