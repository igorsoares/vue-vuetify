<template>
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
</template>

<script>
export default {
  name: "Login",
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

<style scoped></style>
