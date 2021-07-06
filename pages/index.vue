<template>
  <div style="height: 100%">
    <v-row>
      <v-col>
        <v-card class="d-flex align-center justify-space-around text-center">
          <h1 style="width: 100%">Jak chcesz dzisiaj pomóc?</h1>
        </v-card>
      </v-col>
    </v-row>
    <v-row v-for="item in items" :key="item.title">
      <v-col>
        <v-card
          color=""
          class="d-flex align-center justify-space-around text-center"
          ripple
          nuxt
          :to="item.to"
        >
          <v-icon x-large>{{ item.icon }}</v-icon>
          <h1>{{ item.title }}</h1>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          icon: 'mdi-gift',
          title: 'Podaruj rzeczy',
          to: '/gifting',
        },
        {
          icon: 'mdi-hand-heart',
          title: 'Podaruj pieniądze',
          to: '/fundraising',
        },
        {
          icon: 'mdi-apps',
          title: 'Przeglądaj organizacje',
          to: '/orgs',
        },
      ],
    }
  },
}
</script>

<style scoped>
.row,
col {
  height: 25%;
}
.v-card {
  height: 100%;
}
</style>
