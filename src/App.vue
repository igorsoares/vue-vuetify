<template>
  <v-app>
    <!-- APP BAR -->
    <v-app-bar app dark color="#00796B">
      <v-app-bar-title>Vue + Vuetify</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-btn
        v-for="link in links"
        :key="link"
        color="white"
        text
        rounded
        class="my-2"
      >
        {{ link }}
      </v-btn>
    </v-app-bar>

    <!-- LOGIN -->
    <v-main>
      <v-card width="700" class="mx-auto mt-15 pa-10">
        <v-card-title><h1 class="display-1">Login</h1></v-card-title>
        <v-card-text>
          <v-form>
            <v-text-field label="Username" prepend-icon="mdi-account">
            </v-text-field>

            <v-text-field
              label="Password"
              prepend-icon="mdi-lock"
              :append-icon="exibir ? 'mdi-eye-off' : 'mdi-eye'"
              :type="exibir ? 'text' : 'password'"
              @click:append="showHide"
            >
            </v-text-field>
          </v-form>
        </v-card-text>
        <v-card-actions>
          <v-btn color="success">Register</v-btn>
          <v-spacer></v-spacer>
          <v-btn color="info">Login</v-btn>
        </v-card-actions>
      </v-card>
    </v-main>
    <!-- FOOTER -->
    <v-footer color="primary lighten-1" padless>
      <v-row justify="center" no-gutters>
        <v-btn
          v-for="link in links"
          :key="link"
          color="white"
          text
          rounded
          class="my-2"
        >
          {{ link }}
        </v-btn>
        <v-col class="primary lighten-2 py-4 text-center white--text" cols="12">
          {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    exibir: false,
    links: ["Home", "Login", "Cadastro"],
  }),
  methods: {
    showHide() {
      this.exibir = !this.exibir;
    },
  },
};
</script>
