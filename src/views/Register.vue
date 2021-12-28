<template>
  <div class="mx-auto mt-15">
    <v-form width="400" v-model="valid">
      <v-container>
        <v-text-field
          v-model="firstname"
          :rules="nameRules"
          :counter="10"
          label="First name"
          required
        ></v-text-field>

        <v-text-field
          v-model="lastname"
          :rules="nameRules"
          :counter="10"
          label="Last name"
          required
        ></v-text-field>

        <v-text-field
          v-model="email"
          :rules="emailRules"
          label="E-mail"
          required
        ></v-text-field>

        <v-row>
          <v-col cols="2">
            <v-text-field
              @blur="searchCep"
              v-model="cep"
              :rules="cepRules"
              label="Cep"
              required
              v-mask="['#####-###']"
            ></v-text-field>
          </v-col>

          <v-col cols="2">
            <v-text-field
              v-model="logradouro"
              label="Logradouro"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="2">
            <v-text-field
              v-model="localidade"
              label="Localidade"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="6">
            <v-text-field v-model="uf" label="UF" required></v-text-field>
          </v-col>
        </v-row>

        <div class="d-flex justify-center mb-6">
          <v-btn width="300" class="pa-7" rounded elevation="5">Register</v-btn>
        </div>
      </v-container>
    </v-form>
  </div>
</template>

<script>
export default {
  data: () => ({
    valid: false,
    firstname: "",
    lastname: "",
    cep: "",
    logradouro: "",
    localidade: "",
    uf: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => v.length <= 10 || "Name must be less than 10 characters",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+/.test(v) || "E-mail must be valid",
    ],
    cepRules: [(v) => v.length > 8 || "Cep must 8 characters"],
  }),
  methods: {
    async searchCep() {
      const cep = this.cep.replace("-", "");
      if (cep.length === 8) {
        try {
          let url = await `https://viacep.com.br/ws/${cep}/json/`;
          const response = await fetch(url);
          if (response.status != 200) throw new Error("Teste");
          const json = await response.json();
          this.logradouro = json.logradouro;
          this.localidade = json.localidade;
          this.uf = json.uf;
        } catch (e) {
          console.log(e);
        }
      } else {
        this.logradouro = "";
        this.localidade = "";
        this.uf = "";
      }
    },
  },
};
</script>
