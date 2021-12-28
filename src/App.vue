<template>
  <v-app>
    <!-- APP BAR -->
    <v-app-bar app dark color="#00796B">
      <v-app-bar-title>Vue + Vuetify</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-btn
        v-for="(link, i) in links"
        :key="i"
        color="white"
        text
        rounded
        class="my-2"
        :to="link.path"
      >
        {{ link.label }}
      </v-btn>
    </v-app-bar>

    <!-- LOGIN -->
    <v-main>
      <router-view></router-view>
    </v-main>

    <!-- FOOTER -->
    <v-footer color="#004D40" padless>
      <v-row justify="center" no-gutters>
        <v-btn
          v-for="(link, i) in links"
          :key="i"
          color="white"
          text
          rounded
          class="my-2"
          :to="link.path"
        >
          {{ link.label }}
        </v-btn>
        <v-col class="py-4 text-center white--text" cols="12">
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
    links: [
      { label: "Home", path: "/" },
      { label: "Login", path: "/login" },
      { label: "About", path: "/about" },
    ],
  }),
};
</script>
