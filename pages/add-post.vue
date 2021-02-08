<template>
  <v-row class="my-2" align="center" justify="center" style="height: 100%">
    <v-col sm="8" md="8" lg="8" xl="6">
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
        <v-expand-transition>
          <v-slider
            v-if="type == 'fundraising'"
            v-model="price"
            :min="min"
            :max="max"
          ></v-slider>
        </v-expand-transition>
        <v-expand-transition>
          <v-text-field
            v-if="type == 'fundraising'"
            v-model="price"
            label="cena"
            :rules="priceRules"
            suffix="zł"
            outlined
            dense
            required
          ></v-text-field>
        </v-expand-transition>
        <v-form ref="form" v-model="valid" lazy-validation>
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
            height="300"
            :rules="descRules"
            no-resize
            outlined
            dense
            required
          ></v-textarea>
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
      type: '',
      min: 100,
      max: 100000,
      price: 100,
      valid: true,
      title: '',
      desc: '',
      priceRules: [
        (v) => !!v || 'Podaj wartość zbiórki',
        (v) => !isNaN(Number(v)) || 'Podaj liczbę',
        (v) => v >= this.min || 'Cena jest zbyt niska',
        (v) => v <= this.max || 'Cena jest zbyt wysoka',
      ],
      titleRules: [
        (v) => !!v || 'Uzupełnij puste pola',
        (v) => v.length <= 100 || 'Tytuł nie spełnia wymagań',
      ],
      descRules: [(v) => !!v || 'Uzupełnij puste pola'],
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
  letter-spacing: 1px;
  color: #5570d5;
}
</style>
