<template>
  <v-app>
    <v-app-bar color="primary" fixed app>
      <v-toolbar-title class="white--text"> Fundacyjni </v-toolbar-title>
      <v-spacer />
      <v-btn
        v-for="item in items"
        :key="item.title"
        class="ml-5 d-none d-md-flex"
        nuxt
        :to="item.to"
      >
        <v-icon left>{{ item.icon }}</v-icon>
        {{ item.title }}
      </v-btn>
      <v-btn class="ml-5 d-none d-md-flex" nuxt to="/login">
        <v-icon left>mdi-login</v-icon>
        Zaloguj się
      </v-btn>
    </v-app-bar>
    <v-main style="background: #f5f5f5">
      <v-container style="height: 100%">
        <nuxt />
      </v-container>
    </v-main>
    <v-bottom-navigation
      class="d-sm-flex d-md-none"
      app
      background-color="primary"
      dark
    >
      <v-btn v-for="item in items" :key="item.title" nuxt :to="item.to">
        <span>{{ item.title }}</span>

        <v-icon>{{ item.icon }}</v-icon>
      </v-btn>
    </v-bottom-navigation>
    <v-footer color="primary">
      <span class="white--text">&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          icon: 'mdi-apps',
          title: 'Strona główna',
          to: '/',
        },
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
      ],
    }
  },
}
</script>
