<template>
  <v-card nuxt :to="'/posts/' + id">
    <v-img :src="image" max-height="200px"></v-img>
    <v-card-title>Lorem Ipsum</v-card-title>
    <v-card-subtitle> <v-img></v-img> przez Lorem Ipsum </v-card-subtitle>
  </v-card>
</template>

<script>
export default {
  props: {
    image: String,
    id: Number,
  },
}
</script>
