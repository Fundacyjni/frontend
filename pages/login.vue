<template>
  <v-row align="center" justify="center" style="height: 100%">
    <v-col sm="8" md="5" lg="5" xl="3">
      <v-card class="pa-10" elevation="2" outlined style="border-radius: 20px">
        <v-form v-model="valid">
          <v-text-field
            v-model="username"
            :rules="loginRules"
            label="Login"
            placeholder="Login lub email"
            prepend-icon="mdi-account-circle"
            outlined
            dense
          ></v-text-field>
          <v-text-field
            v-model="password"
            :rules="loginRules"
            label="Hasło"
            placeholder="Hasło"
            prepend-icon="mdi-lock"
            outlined
            dense
          ></v-text-field>
          <v-btn
            block
            class="mt-5 green accent-3"
            style="color: #eee"
            :disabled="!valid"
            @click="validate"
          >
            Zaloguj
          </v-btn>
        </v-form>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      valid: false,
      username: '',
      password: '',
      loginRules: [(v) => !!v || 'Uzupełnij puste pola'],
    }
  },
  methods: {
    validate() {
      if (this.valid) alert('Pomyślnie zalogowano :)')
    },
  },
}
</script>

<style scoped>
.v-form,
.container {
  height: 100%;
}
</style>
