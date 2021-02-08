<template>
  <div>
    <v-row justify="center">
      <v-col cols="12">
        <v-text-field
          v-model="searchQuery"
          append-outer-icon="mdi-magnify"
          filled
          clear-icon="mdi-close-circle"
          clearable
          label="Wyszukaj"
          type="text"
          @click:append-outer="sendQuery"
          @click:clear="clearQuery"
        />
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col v-for="post in posts" :key="post.id" cols="12" md="6">
        <item-card
          :id="post.id"
          image="https://picsum.photos/1000"
          class="mb-5"
        />
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        {
          id: 1,
        },
        {
          id: 2,
        },
        {
          id: 3,
        },
        {
          id: 4,
        },
        {
          id: 5,
        },
      ],
      searchQuery: '',
    }
  },
  methods: {
    sendQuery() {
      this.clearQuery()
    },
    clearQuery() {
      this.searchQuery = ''
    },
  },
}
</script>
