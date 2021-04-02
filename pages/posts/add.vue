<template>
  <v-row class="my-2" align="center" justify="center" style="height: 100%">
    <v-col cols="12" md="8" xl="6">
      <v-card class="pa-10" elevation="2" outlined style="border-radius: 20px">
        <v-card-title class="justify-center">Formularz ogłoszenia</v-card-title>
        <v-radio-group v-model="type">
          <template #label>
            <div>Wybierz <strong>typ ogłoszenia</strong></div>
          </template>
          <v-divider class="mb-2"></v-divider>
          <v-radio label="przedmiot" value="gift"></v-radio>
          <v-radio label="zbiórka" value="fundraising"></v-radio>
        </v-radio-group>
        <v-form ref="form" v-model="valid" lazy-validation>
          <v-text-field
            v-model="url"
            label="link do zbiórki"
            outlined
            dense
          ></v-text-field>
          <v-text-field
            v-model="title"
            :counter="100"
            :rules="titleRules"
            label="tytuł"
            outlined
            dense
            required
          ></v-text-field>
          <v-textarea
            v-model="desc"
            label="opis"
            :counter="2000"
            :rules="descRules"
            outlined
            dense
            required
          ></v-textarea>
          <div class="d-sm-flex">
            <v-file-input
              v-model="files"
              small-chips
              multiple
              label="zdjęcia"
              max="2"
            ></v-file-input>
            <v-btn class="ml-8 mt-5" style="color: #eee; background: #5570d5">
              dodaj
            </v-btn>
          </div>
          <v-btn
            block
            class="mt-5 green accent-3"
            style="color: #eee"
            :disabled="!valid"
            @click="validate"
          >
            Opublikuj
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
      type: 'gift',
      price: 100,
      minPrice: 100,
      maxPrice: 100000,
      url: '',
      title: '',
      desc: '',
      files: [],
      valid: true,
      priceRules: [
        (v) => !!v || 'Podaj wartość zbiórki',
        (v) => !isNaN(Number(v)) || 'Podaj liczbę',
        (v) => v >= this.minPrice || 'Cena jest zbyt niska',
        (v) => v <= this.maxPrice || 'Cena jest zbyt wysoka',
      ],
      titleRules: [
        (v) => !!v || 'Uzupełnij puste pola',
        (v) => v.length <= 100 || 'Tytuł nie spełnia wymagań',
      ],
      descRules: [
        (v) => !!v || 'Uzupełnij puste pola',
        (v) => v.length <= 2000 || 'Twój opis jest za długi!',
      ],
    }
  },
  methods: {
    async validate() {
      await this.$refs.form.validate()
      if (this.valid) alert('Pomyślnie opublikowano :)')
    },
  },
}
</script>

<style scoped>
.v-form,
.container {
  height: 100%;
}
.v-card__title {
  text-transform: uppercase;
  font-size: 20px;
  letter-spacing: 1px;
  color: #5570d5;
}
</style>
