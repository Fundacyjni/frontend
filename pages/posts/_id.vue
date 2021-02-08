<template>
  <div>
    <v-overlay z-index="99" :value="overlay">
      <v-img max-width="100vw" max-height="100vh" contain :src="currentImg" />
      <v-btn absolute icon x-large right top @click="overlay = false">
        <v-icon>mdi-close</v-icon>
      </v-btn>
    </v-overlay>
    <v-row justify="center">
      <v-col cols="12" md="8">
        <v-card>
          <v-carousel>
            <v-carousel-item
              v-for="image in images"
              :key="image"
              ripple
              @click="
                overlay = true
                currentImg = image
              "
            >
              <v-img max-height="100%" max-width="100%" :src="image" />
            </v-carousel-item>
          </v-carousel>
          <v-card-title>Lorem Ipsum</v-card-title>
          <div class="px-4 pb-4">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim
            ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
            aliquip ex ea commodo consequat. Duis aute irure dolor in
            reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla
            pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
            culpa qui officia deserunt mollit anim id est laborum.
          </div>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      overlay: false,
      currentImg: '',
      images: [
        'https://picsum.photos/1920/1080',
        'https://picsum.photos/960/720',
        'https://picsum.photos/2160/4096',
        'https://picsum.photos/4000',
        'https://picsum.photos/800/600',
      ],
    }
  },
}
</script>
